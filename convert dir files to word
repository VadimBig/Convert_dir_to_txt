import os
from docx import Document

def convert_to_txt(file_path):
    # Определяем выходное имя файла и открываем его
    output_file_path = f"{os.path.splitext(file_path)[0]}.txt"

    with open(file_path, 'r', encoding='utf-8') as input_file:
        content = input_file.read()

    with open(output_file_path, 'w', encoding='utf-8') as output_file:
        output_file.write(content)

    return output_file_path


def process_directory(directory, output_combined_file):
    with open(output_combined_file, 'w', encoding='utf-8') as combined_file:
        # Проходим по всем файлам и папкам в указанной директории
        for root, dirs, files in os.walk(directory):
            for file in files:
                # Проверяем расширение файла
                if file.endswith(('.cpp', '.py','.h', '.sh', '.pb.cc', '.pb.h', '.proto', '.grpc.pb.cc', '.kt', '.grpc.pb.h', '.gradle')):  # Добавьте нужные форматы
                    file_path = os.path.join(root, file)
                    print(f"Processing file: {file_path}")

                    # Конвертируем файл в txt
                    converted_file_path = convert_to_txt(file_path)

                    # Считываем содержимое преобразованного файла и записываем в общий файл
                    with open(converted_file_path, 'r', encoding='utf-8') as converted_file:
                        combined_content = converted_file.read()
                        combined_file.write(combined_content)
                        combined_file.write("\n")  # Добавляем новую строку между файлами

def convert_txt_to_docx(txt_file_path, docx_file_path):
        # Создаем новый документ Word
    doc = Document()
        # Читаем содержимое текстового файла
    with open(txt_file_path, 'r', encoding='utf-8') as txt_file:

        for line in txt_file:
                # Добавляем каждую строку в документ
            doc.add_paragraph(line.strip())

        # Сохраняем документ в формате .docx
    doc.save(docx_file_path)
    print(f'Файл успешно конвертирован и сохранен как: {docx_file_path}')

if __name__ == "__main__":
    directory_path = "C:/Users/vadim bikbulatov\Downloads\Telegram Desktop\stage5\stage5/mobile-device/app"
    output_file_name = "combined_output1.txt"  # Имя выходного файла с объединённым содержимым
    output_file_name_docx = "combined_output.docx"
    process_directory(directory_path, output_file_name)
    print(f"Обработка завершена. Все данные объединены в файл: {output_file_name}")
    convert_txt_to_docx(output_file_name, output_file_name_docx)
