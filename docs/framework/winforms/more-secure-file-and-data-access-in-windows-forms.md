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
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="44083-102">Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="44083-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="44083-103">.NET Framework, kaynakları ve verileri korumaya yardımcı olmak için izinleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="44083-103">The .NET Framework uses permissions to help protect resources and data.</span></span> <span data-ttu-id="44083-104">Uygulamanızın verileri okuyabildiği veya yazabileceği, uygulamaya verilen izinlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="44083-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="44083-105">Uygulamanız kısmi bir güven ortamında çalıştığında verilerinize erişiminiz olmayabilir veya verilere erişirken kullandığınız yolu değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="44083-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="44083-106">Bir güvenlik kısıtlamasından karşılaştığınızda, iki seçeneğiniz vardır: izni onaylayın (uygulamanıza verildiği varsayılarak) veya kısmi güvende çalışmak için yazılmış özelliğin bir sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="44083-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="44083-107">Aşağıdaki bölümlerde, kısmi güven ortamında çalışan uygulamalardan dosya, veritabanı ve kayıt defteri erişimiyle nasıl çalışılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44083-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44083-108">Varsayılan olarak, ClickOnce dağıtımları oluşturan araçlar, çalıştırdığı bilgisayarlardan tam güven istemek için bu dağıtımları varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44083-108">By default, tools that generate ClickOnce deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="44083-109">Kısmi güvende çalıştırmanın ek güvenlik avantajlarından yararlanmanızı isterseniz, bu varsayılanı Visual Studio 'da veya Windows SDK araçlarından birinde (Mage. exe veya MageUI. exe) değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44083-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the Windows SDK tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="44083-110">Windows Forms güvenliği hakkında daha fazla bilgi için ve uygulamanız için uygun güven düzeyini belirleme hakkında daha fazla bilgi için bkz. [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="44083-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="44083-111">Dosya erişimi</span><span class="sxs-lookup"><span data-stu-id="44083-111">File Access</span></span>  
 <span data-ttu-id="44083-112"><xref:System.Security.Permissions.FileIOPermission> sınıfı .NET Framework dosya ve klasör erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="44083-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the .NET Framework.</span></span> <span data-ttu-id="44083-113">Varsayılan olarak, güvenlik sistemi, <xref:System.Security.Permissions.FileIOPermission> yerel intranet ve Internet bölgeleri gibi kısmi güven ortamlarına vermez.</span><span class="sxs-lookup"><span data-stu-id="44083-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="44083-114">Ancak, uygulamanızın tasarımını değiştirirseniz veya dosyalara erişmek için farklı yöntemler kullanıyorsanız, dosya erişimi gerektiren bir uygulama bu ortamlarda hala çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="44083-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="44083-115">Varsayılan olarak, yerel intranet bölgesine aynı site erişimi ve aynı dizin erişimine sahip olmak, kaynağının sitesine geri bağlanmak ve yükleme dizininden okumak için hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="44083-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="44083-116">Varsayılan olarak, Internet bölgesine yalnızca kendi başlangıç sitesine geri bağlanma hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="44083-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="44083-117">Kullanıcı tarafından belirtilen dosyalar</span><span class="sxs-lookup"><span data-stu-id="44083-117">User-Specified Files</span></span>  
 <span data-ttu-id="44083-118">Dosya erişimi iznine sahip olmayan bir yol, kullanıcıdan <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> sınıfını kullanarak belirli dosya bilgilerini sağlamasını istesağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="44083-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="44083-119">Bu Kullanıcı etkileşimi, uygulamanın özel dosyaları kötü amaçlı olarak yükleyemayacağı veya önemli dosyaların üzerine yazabileceği bazı güvence sağlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="44083-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="44083-120"><xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> ve <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemleri, kullanıcının belirlediği dosyanın dosya akışını açarak okuma ve yazma dosya erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="44083-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="44083-121">Yöntemler, dosyanın yolunu obscuring ile kullanıcının dosyasının korunmasına da yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="44083-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44083-122">Bu izinler, uygulamanızın Internet bölgesinde mi yoksa Intranet bölgesinde mı olduğuna bağlı olarak farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="44083-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="44083-123">Internet bölgesi uygulamaları yalnızca <xref:System.Windows.Forms.OpenFileDialog>kullanabilir, ancak Intranet uygulamalarında sınırsız dosya iletişim kutusu izni vardır.</span><span class="sxs-lookup"><span data-stu-id="44083-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="44083-124"><xref:System.Security.Permissions.FileDialogPermission> sınıfı, uygulamanızın kullanabileceği dosya iletişim kutusu türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="44083-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="44083-125">Aşağıdaki tabloda, her bir <xref:System.Windows.Forms.FileDialog> sınıfını kullanmak için sahip olmanız gereken değer gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44083-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="44083-126">örneği</span><span class="sxs-lookup"><span data-stu-id="44083-126">Class</span></span>|<span data-ttu-id="44083-127">Gerekli erişim değeri</span><span class="sxs-lookup"><span data-stu-id="44083-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> <span data-ttu-id="44083-128"><xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi gerçekten çağrılana kadar belirli izin istenmez.</span><span class="sxs-lookup"><span data-stu-id="44083-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="44083-129">Dosya iletişim kutusu görüntüleme izni, uygulamanıza <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>ve <xref:System.Windows.Forms.SaveFileDialog> sınıflarının tüm üyelerine tam erişim vermez.</span><span class="sxs-lookup"><span data-stu-id="44083-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="44083-130">Her yöntemi çağırmak için gereken tam izinler için, .NET Framework Sınıf Kitaplığı belgelerindeki bu yöntemin başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="44083-130">For the exact permissions that are required to call each method, see the reference topic for that method in the .NET Framework class library documentation.</span></span>  
  
 <span data-ttu-id="44083-131">Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir dosyayı <xref:System.Windows.Forms.RichTextBox> denetiminde açmak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44083-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="44083-132">Örnek <xref:System.Security.Permissions.FileDialogPermission> ve ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="44083-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="44083-133">Örnek, Kaydet özelliğinin devre dışı bırakılıp bırakılmadığını anlamak için <xref:System.Security.SecurityException> nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="44083-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="44083-134">Bu örnek, <xref:System.Windows.Forms.Form> `ButtonOpen`adlı bir <xref:System.Windows.Forms.Button> denetimine ve `RtfBoxMain`adlı bir <xref:System.Windows.Forms.RichTextBox> denetime sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="44083-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44083-135">Kaydet özelliğinin programlama mantığı örnekte gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="44083-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
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
> <span data-ttu-id="44083-136">Görsel C#bölümünde olay işleyicisini etkinleştirmek için kod eklemediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="44083-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="44083-137">Önceki örnekteki kodu kullanarak, aşağıdaki kodda olay işleyicisinin nasıl etkinleştirileceği gösterilmektedir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="44083-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="44083-138">Diğer dosyalar</span><span class="sxs-lookup"><span data-stu-id="44083-138">Other Files</span></span>  
 <span data-ttu-id="44083-139">Bazen, uygulama ayarlarını kalıcı hale getirmeniz gerektiğinde, kullanıcının belirtmeyen dosyaları okumanız veya yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44083-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="44083-140">Yerel intranet ve Internet bölgelerinde, uygulamanızın verileri yerel bir dosyada depolama izni olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="44083-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="44083-141">Ancak, uygulamanız verileri yalıtılmış depolamada depolayabilecektir.</span><span class="sxs-lookup"><span data-stu-id="44083-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="44083-142">Yalıtılmış depolama, verilerin depolandığı gerçek dizin konumlarını içeren depolar adlı bir veya daha fazla yalıtılmış depolama dosyası içeren bir soyut veri bölmesi 'dir (belirli bir depolama konumu değildir).</span><span class="sxs-lookup"><span data-stu-id="44083-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="44083-143"><xref:System.Security.Permissions.FileIOPermission> gibi dosya erişim izinleri gerekli değildir; Bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıfı yalıtılmış depolama izinlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="44083-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="44083-144">Varsayılan olarak, yerel intranet ve Internet bölgelerinde çalışan uygulamalar, yalıtılmış depolama kullanarak veri saklayabilir; Ancak, disk kotası gibi ayarlar farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="44083-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="44083-145">Yalıtılmış depolama hakkında daha fazla bilgi için bkz. [yalıtılmış depolama](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="44083-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="44083-146">Aşağıdaki örnek, bir depoda bulunan bir dosyaya veri yazmak için yalıtılmış depolamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="44083-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="44083-147">Örnek, <xref:System.Security.Permissions.IsolatedStorageFilePermission> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> numaralandırma değeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="44083-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="44083-148">Örnek, <xref:System.Windows.Forms.Button> denetiminin bazı özellik değerlerini, yalıtılmış depolamada bulunan bir dosyaya okumayı ve yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="44083-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="44083-149">`Read` işlevi uygulama başladıktan sonra çağrılır ve uygulama bitmeden önce `Write` işlevi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="44083-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="44083-150">Örnek, `Read` ve `Write` işlevlerinin `MainButton`adlı <xref:System.Windows.Forms.Button> bir denetim içeren bir <xref:System.Windows.Forms.Form> üyeleri olarak var olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="44083-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
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
  
## <a name="database-access"></a><span data-ttu-id="44083-151">Veritabanı Erişimi</span><span class="sxs-lookup"><span data-stu-id="44083-151">Database Access</span></span>  
 <span data-ttu-id="44083-152">Veritabanına erişmek için gereken izinler veritabanı sağlayıcısına göre değişiklik gösterir; Ancak, yalnızca uygun izinlerle çalışan uygulamalar, bir veritabanına veri bağlantısı aracılığıyla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="44083-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="44083-153">Veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="44083-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="44083-154">Uygulamanızın kısmi güvende çalışmasını istediğiniz için doğrudan bir veritabanına erişemiyorsanız, verilerinize erişmek için alternatif bir yöntem olarak Web hizmetini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44083-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="44083-155">Web hizmeti, bir ağ üzerinden programlı bir şekilde erişilebilen bir yazılım parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="44083-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="44083-156">Web hizmetleriyle, uygulamalar, kod grubu bölgelerinde veri paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="44083-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="44083-157">Varsayılan olarak, yerel intranet ve Internet bölgelerindeki uygulamalara kendi kaynak sitelerine erişme hakkı verilir ve bu da aynı sunucuda barındırılan bir Web hizmetini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="44083-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="44083-158">Daha fazla bilgi için bkz. ASP.NET AJAX veya [Windows Communication Foundation](../wcf/index.md) [Web Hizmetleri](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="44083-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="44083-159">Kayıt defteri erişimi</span><span class="sxs-lookup"><span data-stu-id="44083-159">Registry Access</span></span>  
 <span data-ttu-id="44083-160"><xref:System.Security.Permissions.RegistryPermission> sınıfı, işletim sistemi kayıt defterine erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="44083-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="44083-161">Varsayılan olarak, yalnızca yerel olarak çalışan uygulamalar kayıt defterine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="44083-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="44083-162"><xref:System.Security.Permissions.RegistryPermission>, yalnızca bir uygulamaya kayıt erişimini denemeye yönelik hakkı verir; işletim sistemi hala kayıt defteri üzerinde güvenlik uyguladığından, erişimin başarılı olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="44083-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="44083-163">Kısmi güven altında kayıt defterine erişemediği için, verilerinizi depolamanın diğer yöntemlerini bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="44083-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="44083-164">Uygulama ayarlarını depoladığınızda kayıt defteri yerine yalıtılmış depolama kullanın.</span><span class="sxs-lookup"><span data-stu-id="44083-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="44083-165">Yalıtılmış depolama, uygulamaya özgü diğer dosyaları depolamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44083-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="44083-166">Ayrıca, varsayılan olarak bir uygulamaya kendi başlangıç sitesine erişim hakkı verildiği için, sunucu veya kaynak sitesiyle ilgili genel uygulama bilgilerini de saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44083-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44083-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44083-167">See also</span></span>

- [<span data-ttu-id="44083-168">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="44083-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="44083-169">Windows Forms'ta Ek Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="44083-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="44083-170">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="44083-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="44083-171">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="44083-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="44083-172">Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="44083-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="44083-173">MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)</span><span class="sxs-lookup"><span data-stu-id="44083-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
