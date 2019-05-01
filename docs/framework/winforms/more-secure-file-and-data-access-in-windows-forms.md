---
title: Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi
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
ms.openlocfilehash: 557c3296310a7eb3922a6c18b7b3de19ffac953c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802095"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kaynakları ve veri korumaya yardımcı olmak için izinleri kullanır. Burada, uygulamanızın Okuma veya veri yazma uygulamaya verilen izinler bağlıdır. Uygulamanızı bir kısmi güven ortamında çalıştığında, verilerinize erişimi olmayabilir veya verilere erişme şeklini değiştirmek gerekebilir.  
  
 Bir güvenlik kısıtlaması karşılaştığınızda, iki seçeneğiniz vardır: (Bu verilmiş uygulamanıza varsayılarak) izin onay veya kısmi güvende çalışması için yazılmış özelliğinin bir sürümü kullanın. Aşağıdaki bölümlerde, dosya, veritabanı ve kayıt defteri erişimini, kısmi güven ortamında çalışan uygulamalar ile nasıl çalışılacağı açıklanmaktadır.  
  
> [!NOTE]
>  Varsayılan olarak, oluşturma araçları [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımları varsayılan bu dağıtımları isteyen tam güven için çalıştıkları bilgisayarlardan. Kısmi güvende çalışan ek güvenlik avantajları istediğiniz karar verirseniz, bu varsayılan olarak Visual Studio veya birini değiştirmeli [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] araçlarını (Mage.exe veya MageUI.exe). Windows Forms güvenliği hakkında ve uygulamanız için uygun güven düzeyinin nasıl belirleneceği hakkında daha fazla bilgi için bkz: [Windows Forms'ta Güvenliğe genel bakış](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dosya erişimi  
 <xref:System.Security.Permissions.FileIOPermission> Sınıf içindeki dosya ve klasör erişimi denetler [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Varsayılan olarak, güvenlik sistemi yok yetkisi <xref:System.Security.Permissions.FileIOPermission> kısmi güven ortamlara yerel intranet ve Internet bölgelerinden gibi. Ancak, uygulamanızın tasarımını değiştirmek ya da dosyalara erişmek için farklı yöntemler kullanın dosya erişimi gerektiren bir uygulamayı hala bu ortamlarda çalışabilir. Varsayılan olarak, yerel intranet bölgesine aynı site erişimi ve, geri, kaynak siteye bağlanmak ve kendi yükleme dizininden okumak için aynı dizin erişim hakkı verilir. Varsayılan olarak, Internet bölgesi yalnızca verilir, kaynak siteye geri hakkı.  
  
### <a name="user-specified-files"></a>Kullanıcı tarafından belirtilen dosyaları  
 Tek yönlü dağıtılacak dosya erişimi olmaması ile kullanarak belirli dosya bilgileri sağlamak için kullanıcıdan istemek için izindir <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> sınıfı. Bu kullanıcı etkileşimi uygulama erişemeyeceği özel dosyalarını yüklemek veya önemli dosyaların üzerine yazıp, bazı güvence sağlar. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Ve <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> okuma ve yazma dosya erişimi için kullanıcı tarafından belirtilen dosyanın dosya akışı açarak yöntemleri sağlar. Ayrıca yöntemler dosyanın yolu anlaşılması güç tarafından kullanıcının dosyayı koruma yardımcı olur.  
  
> [!NOTE]
>  Bu izinleri uygulamanız Internet bölgesi veya Intranet bölgesi olmasına bağlı olarak değişir. Internet bölgesi uygulamalarına yalnızca kullanma <xref:System.Windows.Forms.OpenFileDialog>bilgileriyse Intranet uygulamalarını dosya iletişim izni sınırsız vardır.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Sınıfını belirtir ne tür bir dosya iletişim kutusu, uygulamanızı kullanabilirsiniz. Aşağıdaki tabloda, her kullanmak için değeri gösterilmektedir <xref:System.Windows.Forms.FileDialog> sınıfı.  
  
|örneği|Gerekli erişim değeri|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Belirli bir izin kadar istenen değil <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi gerçekten çağrılır.  
  
 Dosya iletişim kutusu görüntülemek için izni tüm üyeleri için uygulama tam erişim vermez <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları. Her bir yöntemi çağırmak için gereken tam izinler görmek için bu yönteme yönelik referans konusuna [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sınıf kitaplığı belgeleri.  
  
 Aşağıdaki kod örneğinde <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi, bir kullanıcı tarafından belirtilen dosyaya açmak için bir <xref:System.Windows.Forms.RichTextBox> denetimi. Örnek gerektirir <xref:System.Security.Permissions.FileDialogPermission> ve ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri. Örnek üstesinden nasıl gelineceğini gösterir <xref:System.Security.SecurityException> belirlemek için olup olmadığını kaydetme özelliğini devre dışı bırakılmalıdır. Bu örnekte gerektiren, <xref:System.Windows.Forms.Form> sahip bir <xref:System.Windows.Forms.Button> adlı Denetim `ButtonOpen`ve <xref:System.Windows.Forms.RichTextBox> adlı Denetim `RtfBoxMain`.  
  
> [!NOTE]
>  Programlama mantığı kaydetme örnekte özellik gösterilmez.  
  
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
>  Visual C# içinde olay işleyicisi olanak sağlamak için kod ekleme emin olun. Aşağıdaki kod, önceki örnekte kodunu kullanarak, olay işleyicisi etkinleştirme gösterir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Diğer dosyalar  
 Bazen bir kullanıcı, uygulama ayarları ne zaman kalıcı tutmalıdır gibi belirtmediğinden emin dosyaları okunamıyor veya yazılamıyor gerekir. Yerel intranet ve Internet bölgelerinden, uygulamanızı bir yerel dosya verilerini depolamak için izni yoktur. Ancak, uygulamanız verileri yalıtılmış depolamada depolamak mümkün olacaktır. Yalıtılmış Depolama verilerinin nerede depolanacağını gerçek dizin konumlarını içeren denen bir veya daha fazla yalıtılmış depolama dosyalarını içeren bir soyut bir veri bölmesine (belirli bir depolama konumu değil) var. Dosya erişim izinlerini gibi <xref:System.Security.Permissions.FileIOPermission> gerekli değildir; bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıfı yalıtılmış depolama izinlerini denetler. Varsayılan olarak, yerel intranet ve Internet bölgelerinden çalışan uygulamalar, yalıtılmış depolama kullanarak veri depolayabilir; Ancak, disk kotası gibi ayarları farklılık gösterebilir. Yalıtılmış depolama hakkında daha fazla bilgi için bkz. [yalıtılmış depolama](../../standard/io/isolated-storage.md).  
  
 Aşağıdaki örnek, bir depolama alanında bulunan bir dosyaya veri yazmak için yalıtılmış depolama kullanır. Örnek gerektirir <xref:System.Security.Permissions.IsolatedStorageFilePermission> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> numaralandırma değeri. Örnek okuma ve yazma belirli özellik değerlerini gösterir <xref:System.Windows.Forms.Button> yalıtılmış depolamadaki dosyaya denetimi. `Read` Uygulama başladıktan sonra işlev'in çağrılabilir ve `Write` işlevi uygulama sona ermeden önce çağrılabilir. Örnek gerektiren `Read` ve `Write` işlevleri, üye olarak mevcut bir <xref:System.Windows.Forms.Form> içeren bir <xref:System.Windows.Forms.Button> adlı Denetim `MainButton`.  
  
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
 Bir veritabanına erişmek için gerekli izinlere veritabanı sağlayıcısı'na bağlı olarak değişiklik gösterir; Ancak, uygun izinlerle çalışmakta olan uygulamalar, veri bağlantısı aracılığıyla bir veritabanına erişebilir. Bir veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için bkz: [kod erişimi güvenliği ve ADO.NET](../data/adonet/code-access-security.md).  
  
 Kısmi güvende çalıştırmak için uygulamanızın istediğinden bir veritabanına doğrudan erişemez, verilerinize erişmek bir alternatif anlamına gelir, bir Web hizmetini kullanabilirsiniz. Program aracılığıyla bir ağ üzerinden erişilebilen bir yazılım parçasıdır bir Web hizmetidir. Web hizmetleri sayesinde, uygulamalar, kod grubu bölgeler arasında veri paylaşabilir. Varsayılan olarak, yerel intranet ve Internet bölgelerinden uygulamalar aynı sunucuda barındırılan bir Web hizmeti çağırmak amacıyla sağlayan, kaynak sitelerini erişim hakkı verilir. Daha fazla bilgi için [ASP.NET AJAX Web hizmetlerini](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) veya [Windows Communication Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Registry Access  
 <xref:System.Security.Permissions.RegistryPermission> Sınıfı işletim sistem kayıt defteri erişimi denetler. Varsayılan olarak, yerel olarak çalıştırıyorsanız, yalnızca uygulamalar kayıt defterine erişebilir.  <xref:System.Security.Permissions.RegistryPermission> yalnızca bir uygulama kayıt defteri erişimini deneyin verme hakkı tanımaz; işletim sistemi güvenlik kayıt defterindeki hala zorladığından erişim başarılı olur, garantilemez.  
  
 Kısmi güven altında kayıt defteri erişemediği için diğer yöntemleri, verilerinizi depolamaya gerekebilir. Uygulama ayarlarını depolamak, yalıtılmış depolama yerine kayıt defterini kullanın. Yalıtılmış Depolama, diğer uygulamaya özgü dosyaları depolamak için de kullanılabilir. Varsayılan olarak, uygulamanın kendi kaynak site erişim hakkı verilir çünkü sunucu veya site kaynak, genel uygulama bilgilerini da depolayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Daha Güvenli Yazdırma](more-secure-printing-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
