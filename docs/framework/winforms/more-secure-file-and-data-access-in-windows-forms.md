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
ms.openlocfilehash: 5db6fc886fe53fb60d38471bd463868ce2f37fc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541904"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İzinlerini kaynakları ve veri korumaya yardımcı olmak için kullanır. Burada, uygulamanızın Okuma veya yazma veri uygulamaya verilen izinler bağlıdır. Uygulamanızı bir kısmi güven ortamında çalıştığında, verilerinize erişimi olmayabilir veya verilere erişme şeklini değiştirmek zorunda kalabilirsiniz.  
  
 Bir güvenlik kısıtlama karşılaştığınızda, iki seçeneğiniz vardır: (Bu verildiğini uygulamanıza varsayılarak) izni assert veya kısmi güvende çalışması için yazılmış özelliği sürümünü kullanın. Aşağıdaki bölümlerde dosya, veritabanı ve kayıt defteri erişimi bir kısmi güven ortamında çalışan uygulamalardan ile çalışma konusunda açıklanmaktadır.  
  
> [!NOTE]
>  Varsayılan olarak, oluşturma araçları [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımları varsayılan bu dağıtımlar isteyen tam güven için çalıştıkları bilgisayarlardan. Kısmi güvende çalıştırma ek güvenlik avantajları istemediğinize karar verirseniz, bu varsayılan olarak Visual Studio veya birini değiştirmelisiniz [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Araçları (Mage.exe veya MageUI.exe). Windows Forms güvenliği hakkında ve uygulamanız için uygun güven düzeyini belirleme hakkında daha fazla bilgi için bkz: [Windows Forms'a genel bakış güvenlik](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dosya erişimi  
 <xref:System.Security.Permissions.FileIOPermission> Sınıf denetimleri dosya ve klasör erişim [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Varsayılan olarak, güvenlik sistemi değil vermez <xref:System.Security.Permissions.FileIOPermission> kısmi güven ortamlara yerel intranet ve Internet bölgeleri gibi. Ancak, uygulamanızın tasarımını ya da dosyalara erişim için farklı yöntemler kullanın dosya erişimi gerektiren bir uygulama bu ortamlarda hala çalışabilir. Varsayılan olarak, yerel intranet bölgesine aynı site erişimi ve aynı dizin erişimi, geri, kaynak siteye bağlanmak ve kendi yükleme dizininden okumak için sahip hakkı verilir. Varsayılan olarak, Internet bölgesi yalnızca verilir kendi başlangıç sitesine geri bağlanma hakkı.  
  
### <a name="user-specified-files"></a>Kullanıcı tarafından belirtilen dosyaları  
 Dağıtılacak bir yolu dosya erişimi olmaması ile izin kullanarak belirli dosya bilgilerini sağlamak için kullanıcıdan istemek için şu <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> sınıfı. Bu kullanıcı etkileşimi uygulama kötü amaçlı olarak özel dosyaları yükleyemedi veya önemli dosyaların üzerine yazıp, bazı güvence sağlar, yardımcı olur. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Ve <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> okuma ve yazma dosya erişimi kullanıcı tarafından belirtilen dosya için dosya akışı açarak yöntemleri sağlar. Yöntemleri'de dosyanın yolu anlaşılması güç kullanıcının dosyayı koruyun.  
  
> [!NOTE]
>  Bu izinleri uygulamanızı Internet bölgesi ya da Intranet bölgesi olmasına bağlı olarak değişir. Internet bölgesi uygulamalarına yalnızca kullanabilir <xref:System.Windows.Forms.OpenFileDialog>, Intranet uygulamalarını dosya iletişim izni sınırsız vardır ancak.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Sınıfını belirtir ne tür bir dosya iletişim kutusu, uygulamanızın kullanabilirsiniz. Aşağıdaki tabloda, her kullanılacak olmalıdır değeri gösterilmektedir <xref:System.Windows.Forms.FileDialog> sınıfı.  
  
|örneği|Gerekli erişim değeri|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Belirli bir izin kadar istenen değil <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi gerçekte çağrılır.  
  
 Dosya iletişim kutusu görüntülemek için izni tüm üyeleri için uygulama tam erişim vermez <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları. Her yöntemini çağırmak için gerekli izinleri tam görmek için bu yöntem için başvuru konusunun [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sınıf kitaplığı belgeleri.  
  
 Aşağıdaki kod örneğinde <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi bir kullanıcı tarafından belirtilen dosyaya açmak için bir <xref:System.Windows.Forms.RichTextBox> denetim. Örnek gerektirir <xref:System.Security.Permissions.FileDialogPermission> ve ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri. Bu örnek nasıl işleneceğini gösterir <xref:System.Security.SecurityException> belirlemek için olup olmadığını kaydetme özelliğini devre dışı bırakılmalıdır. Bu örnek gerektiren, <xref:System.Windows.Forms.Form> sahip bir <xref:System.Windows.Forms.Button> adlı Denetim `ButtonOpen`ve bir <xref:System.Windows.Forms.RichTextBox> adlı Denetim `RtfBoxMain`.  
  
> [!NOTE]
>  Programlama mantığı için Kaydet özelliği örnekte gösterilmez.  
  
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
>  Visual C# ' olay işleyicisi olanak sağlamak için kod ekleme emin olun. Aşağıdaki kod, önceki örnek kodu kullanarak, olay işleyicisi etkinleştirme gösterir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Diğer dosyaları  
 Bazen okumak veya kullanıcı, uygulama ayarları ne zaman sürdürülmesi gereken gibi belirtmediğinden emin dosyaları yazmak gerekir. Yerel intranet ve Internet bölgeleri uygulamanızı yerel bir dosyaya veri depolamak için izne sahip değil. Ancak, uygulamanızın yalıtılmış depolamada verileri depolamak mümkün olacaktır. Yalıtılmış Depolama verilerinin depolandığı gerçek dizin konumları içeren depoları olarak adlandırılan bir veya daha fazla yalıtılmış depolama dosyaları içeren bir soyut veri bölme (belirli bir depolama konumu değil) olur. Dosya erişim izinleri gibi <xref:System.Security.Permissions.FileIOPermission> gerekli değildir; bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıfı yalıtılmış depolama için izinleri denetler. Varsayılan olarak, yerel intranet ve Internet bölgeleri çalışmakta olan uygulamalar yalıtılmış depolama kullanarak veri depolayabilir; Ancak, disk kotası gibi ayarları farklılık gösterebilir. Yalıtılmış depolama hakkında daha fazla bilgi için bkz: [yalıtılmış depolama](../../../docs/standard/io/isolated-storage.md).  
  
 Aşağıdaki örnek, bir depolama alanında bulunan bir dosyaya veri yazmak için yalıtılmış depolama kullanır. Örnek gerektirir <xref:System.Security.Permissions.IsolatedStorageFilePermission> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> numaralandırma değeri. Örnek okuma ve yazma belirli özellik değerlerini gösterir <xref:System.Windows.Forms.Button> yalıtılmış depolama dosyasında denetimine. `Read` Uygulama başladıktan sonra işlev'in çağrılabilir ve `Write` işlevi uygulama sona ermeden önce çağrılabilir. Örnek gerektiren `Read` ve `Write` işlevleri üye olarak mevcut bir <xref:System.Windows.Forms.Form> içeren bir <xref:System.Windows.Forms.Button> adlı Denetim `MainButton`.  
  
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
 Bir veritabanına erişmek için gerekli izinleri veritabanı sağlayıcısı bağlı olarak farklılık; Ancak, uygun izinlerle çalışmakta olan uygulamalar bir veritabanı bir veri bağlantısı üzerinden erişebilirsiniz. Bir veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için bkz: [kod erişim güvenliği ve ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Kısmi güvende çalıştırmak için uygulamanızın istediğinden doğrudan bir veritabanı erişemiyorsanız, verilerinize erişmek bir alternatif anlamına gelir gibi bir Web hizmetini kullanabilirsiniz. Bir Web hizmeti, bir ağ üzerinden programlı olarak erişilebilir yazılım parçasıdır. Web Hizmetleri ile uygulamaları kodu Grup dilimlerinde veri paylaşabilir. Varsayılan olarak, yerel intranet ve Internet bölgeleri uygulamalarda sitelerinin bunları aynı sunucu üzerinde barındırılan bir Web hizmetini çağırmak etkinleştirir kaynak erişim hakkı verilir. Daha fazla bilgi için bkz: [ASP.NET AJAX Web hizmetlerinde](http://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) veya [Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Kayıt defteri erişimi  
 <xref:System.Security.Permissions.RegistryPermission> Sınıfı işletim sisteminin kayıt defterine erişim denetler. Varsayılan olarak, yerel olarak çalışan yalnızca uygulamaları kayıt erişebilir.  <xref:System.Security.Permissions.RegistryPermission> yalnızca bir uygulama kayıt defteri erişimi deneyin hakkı verir; işletim sistemi hala kayıt defterindeki güvenlik zorladığından, erişim başarılı olur, garanti etmez.  
  
 Kısmi güven altında kayıt defterine erişemediği için diğer yöntemleri, veri depolamanın bulmak gerekebilir. Uygulama ayarlarını depolamak, yalıtılmış depolama kayıt defteri yerine kullanın. Yalıtılmış Depolama, diğer uygulamaya özgü dosyalarını depolamak için de kullanılabilir. Varsayılan olarak, uygulamanın kendi kaynak site erişim hakkı verilir çünkü sunucu veya siteyle kaynak, genel uygulama bilgilerini de depolayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Daha Güvenli Yazdırma](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Windows Forms'ta Ek Güvenlik Konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Windows Forms'ta Güvenliğe Genel Bakış](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms Güvenliği](../../../docs/framework/winforms/windows-forms-security.md)  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
