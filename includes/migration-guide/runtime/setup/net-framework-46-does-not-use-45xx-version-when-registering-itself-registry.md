### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 4.5.x.x sürüm kendisini kayıt defterine kaydedilirken kullanmaz

|   |   |
|---|---|
|Ayrıntılar|Sürüm anahtarı bir bekleyebilirsiniz gibi kayıt defterinde ayarlayın (adresindeki <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) için .NET Framework 4.6 '4.6 ile', '4.5' değil başlar. 4.6 bir yeni olası sürümüdür ve önceki 4.5.x ile uyumlu bir serbest anlamak için hangi .NET Framework sürümlerinin bir makinede yüklü olduğunu öğrenmek için bu kayıt defteri anahtarları bağımlı uygulamalar güncelleştirilmesi gerekir.|
|Öneri|.NET Framework 4.5 için yoklama güncelleştirme uygulamalar ayrıca 4.6 kabul etmek 4.5 kayıt defteri anahtarları için bakarak yükleyin.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

