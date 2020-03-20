---
title: Daha Güvenli Dosya ve Veri Erişimi
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
ms.openlocfilehash: a29c2f7137440e64fbf8095f77d5d10d0505bc2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185896"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi
.NET Framework, kaynakların ve verilerin korunmasına yardımcı olmak için izinleri kullanır. Uygulamanızın verileri nerede okuyabileceği veya yazabileceği, uygulamaya verilen izinlere bağlıdır. Uygulamanız kısmi bir güven ortamında çalıştığında, verilerinize erişiminiz olmayabilir veya verilere erişim şeklinizi değiştirmeniz gerekebilir.  
  
 Bir güvenlik kısıtlaması ile karşılaştığınızda iki seçeneğiniz vardır: izni nizi belirtin (uygulamanız için verildiğini varsayarak) veya kısmi güven içinde çalışmak üzere yazılmış özelliğin bir sürümünü kullanın. Aşağıdaki bölümlerde, kısmi bir güven ortamında çalışan uygulamalardan dosya, veritabanı ve kayıt defteri erişimiyle nasıl çalışılalış edilir.  
  
> [!NOTE]
> Varsayılan olarak, ClickOnce dağıtımları oluşturan araçlar, bu dağıtımları çalıştırdıkları bilgisayarlardan Tam Güven istemeye varsayılan olarak kullanır. Kısmi güven içinde çalıştırmanın ek güvenlik avantajlarını istediğinize karar verirseniz, visual studio'da veya Windows SDK araçlarından (Mage.exe veya MageUI.exe) birinde bu varsayılanı değiştirmeniz gerekir. Windows Forms güvenliği ve uygulamanız için uygun güven düzeyini belirleme hakkında daha fazla bilgi için [Windows Formlarına Genel Bakış'ta Güvenlik'e](security-in-windows-forms-overview.md)bakın.  
  
## <a name="file-access"></a>Dosya Erişimi  
 Sınıf,.NET <xref:System.Security.Permissions.FileIOPermission> Framework'de dosya ve klasör erişimini denetler. Varsayılan olarak, güvenlik sistemi yerel <xref:System.Security.Permissions.FileIOPermission> intranet ve Internet bölgeleri gibi kısmi güven ortamlarına izin vermez. Ancak, uygulamanızın tasarımını değiştirirseniz veya dosyalara erişmek için farklı yöntemler kullanırsanız, dosya erişimi gerektiren bir uygulama bu ortamlarda çalışmaya devam edebilir. Varsayılan olarak, yerel intranet bölgesine aynı site erişimine ve aynı dizin erişimine sahip olmak, kaynağının sitesine geri bağlanmak ve yükleme dizininden okuma hakkı verilir. Varsayılan olarak, Internet bölgesine yalnızca kaynağının bulunduğu siteye yeniden bağlanma hakkı verilir.  
  
### <a name="user-specified-files"></a>Kullanıcı Tarafından Belirtilen Dosyalar  
 Dosya erişim izni olmamasıyla başa çıkmanın bir yolu, kullanıcıdan sınıfı <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.SaveFileDialog> veya sınıfı kullanarak belirli dosya bilgilerini sağlaması için istekte bulunmaktır. Bu kullanıcı etkileşimi, uygulamanın özel dosyaları kötü amaçlı olarak yükleyemeyeceğine veya önemli dosyaların üzerine yazamayacağına dair bazı güvenceler sağlamaya yardımcı olur. Ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemler, kullanıcının belirttiği dosya için dosya akışını açarak dosya erişimini okuma ve yazma sağlar. Yöntemler, dosyanın yolunu gizleyen kullanıcının dosyasını korumaya da yardımcı olur.  
  
> [!NOTE]
> Bu izinler, uygulamanızın Internet bölgesinde mi yoksa Intranet bölgesinde mi olduğuna bağlı olarak değişir. Internet bölgesi uygulamaları yalnızca <xref:System.Windows.Forms.OpenFileDialog>Intranet uygulamaları sınırsız dosya iletişim iznine sahipken, yalnızca ,  
  
 Sınıf, <xref:System.Security.Permissions.FileDialogPermission> uygulamanızın ne tür bir dosya iletişim kutusu kullanabileceğini belirtir. Aşağıdaki tablo, her <xref:System.Windows.Forms.FileDialog> sınıfı kullanmanız gereken değeri gösterir.  
  
|Sınıf|Gerekli erişim değeri|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> Yöntem gerçekten çağrılana <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> kadar özel izin istenmez.  
  
 Dosya iletişim kutusunu görüntüleme <xref:System.Windows.Forms.FileDialog>izni, başvurunuza , ve <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.SaveFileDialog> sınıfların tüm üyelerine tam erişim sağlamaz. Her yöntemi çağırmak için gereken tam izinler için,.NET Framework sınıf kitaplığı belgelerinde bu yöntemiçin başvuru konusuna bakın.  
  
 Aşağıdaki kod örneği, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> kullanıcı tarafından belirtilen bir dosyayı <xref:System.Windows.Forms.RichTextBox> denetime açmak için yöntemi kullanır. Örnek ve <xref:System.Security.Permissions.FileDialogPermission> ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri gerektirir. Örnek, kaydet özelliğinin <xref:System.Security.SecurityException> devre dışı bırakılmalı mı belirleneceğini belirlemek için nasıl işleyeceğini gösterir. Bu örnek, <xref:System.Windows.Forms.Form> sizin <xref:System.Windows.Forms.Button> adlı `ButtonOpen`bir denetim <xref:System.Windows.Forms.RichTextBox> ve `RtfBoxMain`adlı bir denetim gerektirir.  
  
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
> Visual C#'da, olay işleyicisini etkinleştirmek için kod eklediğinizden emin olun. Önceki örnekteki kodu kullanarak, aşağıdaki kod olay işleyicisinin nasıl etkinleştirilen gösterir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Diğer Dosyalar  
 Bazen, uygulama ayarlarını ne zaman devam ettirebilmeniz gerektiği gibi, kullanıcının belirtmediği dosyaları okumanız veya yazmanız gerekir. Yerel intranet ve Internet bölgelerinde, uygulamanızın verileri yerel bir dosyada depolama izni olmaz. Ancak, uygulamanız verileri yalıtılmış depolamada depolayabiliyor. Yalıtılmış depolama, verilerin depolandığı gerçek dizin konumlarını içeren, mağazalar adı verilen bir veya daha fazla yalıtılmış depolama dosyası içeren soyut bir veri bölmesidir (belirli bir depolama konumu değildir). Gibi <xref:System.Security.Permissions.FileIOPermission> dosya erişim izinleri gerekli değildir; bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıf yalıtılmış depolama izinlerini denetler. Varsayılan olarak, yerel intranet ve Internet bölgelerinde çalışan uygulamalar yalıtılmış depolama kullanarak veri depolayabilir; ancak, disk kotası gibi ayarlar değişebilir. Yalıtılmış depolama hakkında daha fazla bilgi için [yalıtılmış Depolama'ya](../../standard/io/isolated-storage.md)bakın.  
  
 Aşağıdaki örnek, bir mağazada bulunan bir dosyaya veri yazmak için yalıtılmış depolama kullanır. Örnek ve <xref:System.Security.Permissions.IsolatedStorageFilePermission> numaralandırma değeri gerektirir. <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> Örnek, denetimin <xref:System.Windows.Forms.Button> belirli özellik değerlerini yalıtılmış depolamadaki bir dosyaya okumayı ve yazmayı gösterir. İşlev, `Read` uygulama başladıktan sonra `Write` çağrılır ve işlev uygulama sona ermeden önce çağrılır. Örnek, `Read` ve `Write` işlevleri adlı <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Button> `MainButton`bir denetim içeren bir üye olarak var gerektirir.  
  
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
  
## <a name="database-access"></a>Veritabanı Erişimi  
 Veritabanına erişmek için gereken izinler veritabanı sağlayıcısına göre değişir; ancak, yalnızca uygun izinlerle çalışan uygulamalar bir veritabanına veri bağlantısı üzerinden erişebilir. Veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için [Kod Erişim Güvenliği ve ADO.NET](../data/adonet/code-access-security.md)bakın.  
  
 Uygulamanızın kısmi güven içinde çalışmasını istediğiniz için bir veritabanına doğrudan erişemiyorsanız, verilerinize erişmek için alternatif bir araç olarak bir Web hizmeti kullanabilirsiniz. Web hizmeti, bir ağ üzerinden programlanabilir bir yazılım dır. Web hizmetleriyle, uygulamalar verileri kod grubu bölgeleri arasında paylaşabilir. Varsayılan olarak, yerel intranet ve Internet bölgelerindeki uygulamalara, aynı sunucuda barındırılan bir Web hizmetini aramalarına olanak tanıyan başlangıç sitelerine erişme hakkı verilir. Daha fazla bilgi için ASP.NET AJAX veya [Windows Communication Foundation](../wcf/index.md)web [hizmetlerine](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) bakın.  
  
## <a name="registry-access"></a>Kayıt Defteri Erişimi  
 Sınıf, <xref:System.Security.Permissions.RegistryPermission> işletim sistemi kayıt defterine erişimi denetler. Varsayılan olarak, yalnızca yerel olarak çalışan uygulamalar kayıt defterine erişebilir.  <xref:System.Security.Permissions.RegistryPermission>yalnızca bir uygulamaya kayıt defterierişimini deneme hakkı verir; işletim sistemi kayıt defterinde güvenliği hala zorladığı için erişimin başarılı olacağını garanti etmez.  
  
 Kayıt defterine kısmi güven altında erişemediğiniz için, verilerinizi depolamak için başka yöntemler bulmanız gerekebilir. Uygulama ayarlarını depolarken, kayıt defteri yerine yalıtılmış depolama yı kullanın. Yalıtılmış depolama, uygulamaya özgü diğer dosyaları depolamak için de kullanılabilir. Varsayılan olarak bir uygulamaya sitenin menşei olan siteye erişim hakkı verildiğinden, sunucu veya kaynak site hakkında genel uygulama bilgilerini de depolayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Daha Güvenli Yazdırma](more-secure-printing-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
