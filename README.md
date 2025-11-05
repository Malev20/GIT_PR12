# Практическая работа №12 (1 уровень)

## Мальев Никита Иванович (2 уровень)
***Обо мне***

*«Учение - это светлый путь к познанию.» — Артур Шопенгауэр*😈

~~Зачеркнутый текст~~

**Студент Заволжского автоматорного техникума.** 

__Специальность 09.02.07__

### ИС-22А (3 уровень)
![Фото](https://github.com/Malev20/GIT_PR12/blob/main/IS22A_Malev_NI.png)

[Клик 🎦](https://github.com/Malev20/GIT_PR12)

`
private void RestoreDatabaseStructure()
        {
            try
            {
                OpenFileDialog dialog = new OpenFileDialog();
                dialog.Filter = "SQL files (*.sql)|*.sql";

                if (dialog.ShowDialog() == DialogResult.OK)
                {
                    MySqlConnection conn = new MySqlConnection(connStr);
                    conn.Open();

                    string[] lines = File.ReadAllLines(dialog.FileName);
                    string currentCommand = "";

                    foreach (string line in lines)
                    {
                        if (string.IsNullOrWhiteSpace(line) || line.Trim().StartsWith("--"))
                            continue;

                        currentCommand += line;

                        if (line.Trim().EndsWith(";"))
                        {
                            if (!string.IsNullOrWhiteSpace(currentCommand.Trim(';', ' ', '\t', '\r', '\n')))
                            {
                                MySqlCommand cmd = new MySqlCommand(currentCommand, conn);
                                cmd.ExecuteNonQuery();
                            }
                            currentCommand = "";
                        }
                    }

                    conn.Close();
                    MessageBox.Show("Структура БД была восстановлена!");
                    SelectTable.Items.Clear();
                    FillComboBox();
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show("Ошибка: " + ex.Message);
            }
        }`
