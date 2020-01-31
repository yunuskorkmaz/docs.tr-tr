---
title: Daha güvenli dosya ve veri erişimi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 49ba1919f68f35e9d72b012540b785e05c307c39
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743754"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi
.NET Framework, kaynakları ve verileri korumaya yardımcı olmak için izinleri kullanır. Uygulamanızın verileri okuyabildiği veya yazabileceği, uygulamaya verilen izinlere bağlıdır. Uygulamanız kısmi bir güven ortamında çalıştığında verilerinize erişiminiz olmayabilir veya verilere erişirken kullandığınız yolu değiştirmeniz gerekebilir.  
  
 Bir güvenlik kısıtlamasından karşılaştığınızda, iki seçeneğiniz vardır: izni onaylayın (uygulamanıza verildiği varsayılarak) veya kısmi güvende çalışmak için yazılmış özelliğin bir sürümünü kullanın. Aşağıdaki bölümlerde, kısmi güven ortamında çalışan uygulamalardan dosya, veritabanı ve kayıt defteri erişimiyle nasıl çalışılacağı açıklanmaktadır.  
  
> [!NOTE]
> Varsayılan olarak, ClickOnce dağıtımları oluşturan araçlar, çalıştırdığı bilgisayarlardan tam güven istemek için bu dağıtımları varsayılan olarak oluşturur. Kısmi güvende çalıştırmanın ek güvenlik avantajlarından yararlanmanızı isterseniz, bu varsayılanı Visual Studio 'da veya Windows SDK araçlarından birinde (Mage. exe veya MageUI. exe) değiştirmeniz gerekir. Windows Forms güvenliği hakkında daha fazla bilgi için ve uygulamanız için uygun güven düzeyini belirleme hakkında daha fazla bilgi için bkz. [Security in Windows Forms Overview](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dosya erişimi  
 <xref:System.Security.Permissions.FileIOPermission> sınıfı .NET Framework dosya ve klasör erişimini denetler. Varsayılan olarak, güvenlik sistemi, <xref:System.Security.Permissions.FileIOPermission> yerel intranet ve Internet bölgeleri gibi kısmi güven ortamlarına vermez. Ancak, uygulamanızın tasarımını değiştirirseniz veya dosyalara erişmek için farklı yöntemler kullanıyorsanız, dosya erişimi gerektiren bir uygulama bu ortamlarda hala çalışabilir. Varsayılan olarak, yerel intranet bölgesine aynı site erişimi ve aynı dizin erişimine sahip olmak, kaynağının sitesine geri bağlanmak ve yükleme dizininden okumak için hakkı verilir. Varsayılan olarak, Internet bölgesine yalnızca kendi başlangıç sitesine geri bağlanma hakkı verilir.  
  
### <a name="user-specified-files"></a>Kullanıcı tarafından belirtilen dosyalar  
 Dosya erişimi iznine sahip olmayan bir yol, kullanıcıdan <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> sınıfını kullanarak belirli dosya bilgilerini sağlamasını istesağlamaktır. Bu Kullanıcı etkileşimi, uygulamanın özel dosyaları kötü amaçlı olarak yükleyemayacağı veya önemli dosyaların üzerine yazabileceği bazı güvence sağlanmasına yardımcı olur. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> ve <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemleri, kullanıcının belirlediği dosyanın dosya akışını açarak okuma ve yazma dosya erişimi sağlar. Yöntemler, dosyanın yolunu obscuring ile kullanıcının dosyasının korunmasına da yardımcı olur.  
  
> [!NOTE]
> Bu izinler, uygulamanızın Internet bölgesinde mi yoksa Intranet bölgesinde mı olduğuna bağlı olarak farklılık gösterir. Internet bölgesi uygulamaları yalnızca <xref:System.Windows.Forms.OpenFileDialog>kullanabilir, ancak Intranet uygulamalarında sınırsız dosya iletişim kutusu izni vardır.  
  
 <xref:System.Security.Permissions.FileDialogPermission> sınıfı, uygulamanızın kullanabileceği dosya iletişim kutusu türünü belirtir. Aşağıdaki tabloda, her bir <xref:System.Windows.Forms.FileDialog> sınıfını kullanmak için sahip olmanız gereken değer gösterilmektedir.  
  
|Sınıf|Gerekli erişim değeri|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi gerçekten çağrılana kadar belirli izin istenmez.  
  
 Dosya iletişim kutusu görüntüleme izni, uygulamanıza <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>ve <xref:System.Windows.Forms.SaveFileDialog> sınıflarının tüm üyelerine tam erişim vermez. Her yöntemi çağırmak için gereken tam izinler için, .NET Framework Sınıf Kitaplığı belgelerindeki bu yöntemin başvuru konusuna bakın.  
  
 Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir dosyayı <xref:System.Windows.Forms.RichTextBox> denetiminde açmak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemini kullanır. Örnek <xref:System.Security.Permissions.FileDialogPermission> ve ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri gerektirir. Örnek, Kaydet özelliğinin devre dışı bırakılıp bırakılmadığını anlamak için <xref:System.Security.SecurityException> nasıl işleneceğini gösterir. Bu örnek, <xref:System.Windows.Forms.Form> `ButtonOpen`adlı bir <xref:System.Windows.Forms.Button> denetimine ve `RtfBoxMain`adlı bir <xref:System.Windows.Forms.RichTextBox> denetime sahip olmasını gerektirir.  
  
> [!NOTE]
> Kaydet özelliğinin programlama mantığı örnekte gösterilmez.  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
> Görsel C#bölümünde olay işleyicisini etkinleştirmek için kod eklemediğinizden emin olun. Önceki örnekteki kodu kullanarak, aşağıdaki kodda olay işleyicisinin nasıl etkinleştirileceği gösterilmektedir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Diğer dosyalar  
 Bazen, uygulama ayarlarını kalıcı hale getirmeniz gerektiğinde, kullanıcının belirtmeyen dosyaları okumanız veya yazmanız gerekir. Yerel intranet ve Internet bölgelerinde, uygulamanızın verileri yerel bir dosyada depolama izni olmayacaktır. Ancak, uygulamanız verileri yalıtılmış depolamada depolayabilecektir. Yalıtılmış depolama, verilerin depolandığı gerçek dizin konumlarını içeren depolar adlı bir veya daha fazla yalıtılmış depolama dosyası içeren bir soyut veri bölmesi 'dir (belirli bir depolama konumu değildir). <xref:System.Security.Permissions.FileIOPermission> gibi dosya erişim izinleri gerekli değildir; Bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıfı yalıtılmış depolama izinlerini denetler. Varsayılan olarak, yerel intranet ve Internet bölgelerinde çalışan uygulamalar, yalıtılmış depolama kullanarak veri saklayabilir; Ancak, disk kotası gibi ayarlar farklılık gösterebilir. Yalıtılmış depolama hakkında daha fazla bilgi için bkz. [yalıtılmış depolama](../../standard/io/isolated-storage.md).  
  
 Aşağıdaki örnek, bir depoda bulunan bir dosyaya veri yazmak için yalıtılmış depolamayı kullanır. Örnek, <xref:System.Security.Permissions.IsolatedStorageFilePermission> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> numaralandırma değeri gerektirir. Örnek, <xref:System.Windows.Forms.Button> denetiminin bazı özellik değerlerini, yalıtılmış depolamada bulunan bir dosyaya okumayı ve yazmayı gösterir. `Read` işlevi uygulama başladıktan sonra çağrılır ve uygulama bitmeden önce `Write` işlevi çağırılır. Örnek, `Read` ve `Write` işlevlerinin `MainButton`adlı <xref:System.Windows.Forms.Button> bir denetim içeren bir <xref:System.Windows.Forms.Form> üyeleri olarak var olmasını gerektirir.  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a>Veritabanı erişimi  
 Veritabanına erişmek için gereken izinler veritabanı sağlayıcısına göre değişiklik gösterir; Ancak, yalnızca uygun izinlerle çalışan uygulamalar, bir veritabanına veri bağlantısı aracılığıyla erişebilir. Veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](../data/adonet/code-access-security.md).  
  
 Uygulamanızın kısmi güvende çalışmasını istediğiniz için doğrudan bir veritabanına erişemiyorsanız, verilerinize erişmek için alternatif bir yöntem olarak Web hizmetini kullanabilirsiniz. Web hizmeti, bir ağ üzerinden programlı bir şekilde erişilebilen bir yazılım parçasıdır. Web hizmetleriyle, uygulamalar, kod grubu bölgelerinde veri paylaşabilir. Varsayılan olarak, yerel intranet ve Internet bölgelerindeki uygulamalara kendi kaynak sitelerine erişme hakkı verilir ve bu da aynı sunucuda barındırılan bir Web hizmetini çağırabilir. Daha fazla bilgi için bkz. ASP.NET AJAX veya [Windows Communication Foundation](../wcf/index.md) [Web Hizmetleri](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) .  
  
## <a name="registry-access"></a>Kayıt defteri erişimi  
 <xref:System.Security.Permissions.RegistryPermission> sınıfı, işletim sistemi kayıt defterine erişimi denetler. Varsayılan olarak, yalnızca yerel olarak çalışan uygulamalar kayıt defterine erişebilir.  <xref:System.Security.Permissions.RegistryPermission>, yalnızca bir uygulamaya kayıt erişimini denemeye yönelik hakkı verir; işletim sistemi hala kayıt defteri üzerinde güvenlik uyguladığından, erişimin başarılı olacağını garanti etmez.  
  
 Kısmi güven altında kayıt defterine erişemediği için, verilerinizi depolamanın diğer yöntemlerini bulmanız gerekebilir. Uygulama ayarlarını depoladığınızda kayıt defteri yerine yalıtılmış depolama kullanın. Yalıtılmış depolama, uygulamaya özgü diğer dosyaları depolamak için de kullanılabilir. Ayrıca, varsayılan olarak bir uygulamaya kendi başlangıç sitesine erişim hakkı verildiği için, sunucu veya kaynak sitesiyle ilgili genel uygulama bilgilerini de saklayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Daha Güvenli Yazdırma](more-secure-printing-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
