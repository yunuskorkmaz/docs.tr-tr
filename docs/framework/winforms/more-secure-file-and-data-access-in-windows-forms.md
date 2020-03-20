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
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="d5d73-102">Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="d5d73-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="d5d73-103">.NET Framework, kaynakların ve verilerin korunmasına yardımcı olmak için izinleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-103">The .NET Framework uses permissions to help protect resources and data.</span></span> <span data-ttu-id="d5d73-104">Uygulamanızın verileri nerede okuyabileceği veya yazabileceği, uygulamaya verilen izinlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="d5d73-105">Uygulamanız kısmi bir güven ortamında çalıştığında, verilerinize erişiminiz olmayabilir veya verilere erişim şeklinizi değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="d5d73-106">Bir güvenlik kısıtlaması ile karşılaştığınızda iki seçeneğiniz vardır: izni nizi belirtin (uygulamanız için verildiğini varsayarak) veya kısmi güven içinde çalışmak üzere yazılmış özelliğin bir sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="d5d73-107">Aşağıdaki bölümlerde, kısmi bir güven ortamında çalışan uygulamalardan dosya, veritabanı ve kayıt defteri erişimiyle nasıl çalışılalış edilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d73-108">Varsayılan olarak, ClickOnce dağıtımları oluşturan araçlar, bu dağıtımları çalıştırdıkları bilgisayarlardan Tam Güven istemeye varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-108">By default, tools that generate ClickOnce deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="d5d73-109">Kısmi güven içinde çalıştırmanın ek güvenlik avantajlarını istediğinize karar verirseniz, visual studio'da veya Windows SDK araçlarından (Mage.exe veya MageUI.exe) birinde bu varsayılanı değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the Windows SDK tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="d5d73-110">Windows Forms güvenliği ve uygulamanız için uygun güven düzeyini belirleme hakkında daha fazla bilgi için [Windows Formlarına Genel Bakış'ta Güvenlik'e](security-in-windows-forms-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="d5d73-111">Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="d5d73-111">File Access</span></span>  
 <span data-ttu-id="d5d73-112">Sınıf,.NET <xref:System.Security.Permissions.FileIOPermission> Framework'de dosya ve klasör erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="d5d73-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the .NET Framework.</span></span> <span data-ttu-id="d5d73-113">Varsayılan olarak, güvenlik sistemi yerel <xref:System.Security.Permissions.FileIOPermission> intranet ve Internet bölgeleri gibi kısmi güven ortamlarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d5d73-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="d5d73-114">Ancak, uygulamanızın tasarımını değiştirirseniz veya dosyalara erişmek için farklı yöntemler kullanırsanız, dosya erişimi gerektiren bir uygulama bu ortamlarda çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="d5d73-115">Varsayılan olarak, yerel intranet bölgesine aynı site erişimine ve aynı dizin erişimine sahip olmak, kaynağının sitesine geri bağlanmak ve yükleme dizininden okuma hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="d5d73-116">Varsayılan olarak, Internet bölgesine yalnızca kaynağının bulunduğu siteye yeniden bağlanma hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="d5d73-117">Kullanıcı Tarafından Belirtilen Dosyalar</span><span class="sxs-lookup"><span data-stu-id="d5d73-117">User-Specified Files</span></span>  
 <span data-ttu-id="d5d73-118">Dosya erişim izni olmamasıyla başa çıkmanın bir yolu, kullanıcıdan sınıfı <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.SaveFileDialog> veya sınıfı kullanarak belirli dosya bilgilerini sağlaması için istekte bulunmaktır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="d5d73-119">Bu kullanıcı etkileşimi, uygulamanın özel dosyaları kötü amaçlı olarak yükleyemeyeceğine veya önemli dosyaların üzerine yazamayacağına dair bazı güvenceler sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d5d73-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="d5d73-120">Ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemler, kullanıcının belirttiği dosya için dosya akışını açarak dosya erişimini okuma ve yazma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d73-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="d5d73-121">Yöntemler, dosyanın yolunu gizleyen kullanıcının dosyasını korumaya da yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d5d73-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d73-122">Bu izinler, uygulamanızın Internet bölgesinde mi yoksa Intranet bölgesinde mi olduğuna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="d5d73-123">Internet bölgesi uygulamaları yalnızca <xref:System.Windows.Forms.OpenFileDialog>Intranet uygulamaları sınırsız dosya iletişim iznine sahipken, yalnızca ,</span><span class="sxs-lookup"><span data-stu-id="d5d73-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="d5d73-124">Sınıf, <xref:System.Security.Permissions.FileDialogPermission> uygulamanızın ne tür bir dosya iletişim kutusu kullanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="d5d73-125">Aşağıdaki tablo, her <xref:System.Windows.Forms.FileDialog> sınıfı kullanmanız gereken değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="d5d73-126">Sınıf</span><span class="sxs-lookup"><span data-stu-id="d5d73-126">Class</span></span>|<span data-ttu-id="d5d73-127">Gerekli erişim değeri</span><span class="sxs-lookup"><span data-stu-id="d5d73-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> <span data-ttu-id="d5d73-128">Yöntem gerçekten çağrılana <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> kadar özel izin istenmez.</span><span class="sxs-lookup"><span data-stu-id="d5d73-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="d5d73-129">Dosya iletişim kutusunu görüntüleme <xref:System.Windows.Forms.FileDialog>izni, başvurunuza , ve <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.SaveFileDialog> sınıfların tüm üyelerine tam erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d5d73-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="d5d73-130">Her yöntemi çağırmak için gereken tam izinler için,.NET Framework sınıf kitaplığı belgelerinde bu yöntemiçin başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-130">For the exact permissions that are required to call each method, see the reference topic for that method in the .NET Framework class library documentation.</span></span>  
  
 <span data-ttu-id="d5d73-131">Aşağıdaki kod örneği, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> kullanıcı tarafından belirtilen bir dosyayı <xref:System.Windows.Forms.RichTextBox> denetime açmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="d5d73-132">Örnek ve <xref:System.Security.Permissions.FileDialogPermission> ilişkili <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> numaralandırma değeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="d5d73-133">Örnek, kaydet özelliğinin <xref:System.Security.SecurityException> devre dışı bırakılmalı mı belirleneceğini belirlemek için nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="d5d73-134">Bu örnek, <xref:System.Windows.Forms.Form> sizin <xref:System.Windows.Forms.Button> adlı `ButtonOpen`bir denetim <xref:System.Windows.Forms.RichTextBox> ve `RtfBoxMain`adlı bir denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d73-135">Kaydet özelliğinin programlama mantığı örnekte gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d5d73-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
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
> <span data-ttu-id="d5d73-136">Visual C#'da, olay işleyicisini etkinleştirmek için kod eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5d73-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="d5d73-137">Önceki örnekteki kodu kullanarak, aşağıdaki kod olay işleyicisinin nasıl etkinleştirilen gösterir.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="d5d73-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="d5d73-138">Diğer Dosyalar</span><span class="sxs-lookup"><span data-stu-id="d5d73-138">Other Files</span></span>  
 <span data-ttu-id="d5d73-139">Bazen, uygulama ayarlarını ne zaman devam ettirebilmeniz gerektiği gibi, kullanıcının belirtmediği dosyaları okumanız veya yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="d5d73-140">Yerel intranet ve Internet bölgelerinde, uygulamanızın verileri yerel bir dosyada depolama izni olmaz.</span><span class="sxs-lookup"><span data-stu-id="d5d73-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="d5d73-141">Ancak, uygulamanız verileri yalıtılmış depolamada depolayabiliyor.</span><span class="sxs-lookup"><span data-stu-id="d5d73-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="d5d73-142">Yalıtılmış depolama, verilerin depolandığı gerçek dizin konumlarını içeren, mağazalar adı verilen bir veya daha fazla yalıtılmış depolama dosyası içeren soyut bir veri bölmesidir (belirli bir depolama konumu değildir).</span><span class="sxs-lookup"><span data-stu-id="d5d73-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="d5d73-143">Gibi <xref:System.Security.Permissions.FileIOPermission> dosya erişim izinleri gerekli değildir; bunun yerine, <xref:System.Security.Permissions.IsolatedStoragePermission> sınıf yalıtılmış depolama izinlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="d5d73-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="d5d73-144">Varsayılan olarak, yerel intranet ve Internet bölgelerinde çalışan uygulamalar yalıtılmış depolama kullanarak veri depolayabilir; ancak, disk kotası gibi ayarlar değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="d5d73-145">Yalıtılmış depolama hakkında daha fazla bilgi için [yalıtılmış Depolama'ya](../../standard/io/isolated-storage.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="d5d73-146">Aşağıdaki örnek, bir mağazada bulunan bir dosyaya veri yazmak için yalıtılmış depolama kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="d5d73-147">Örnek ve <xref:System.Security.Permissions.IsolatedStorageFilePermission> numaralandırma değeri gerektirir. <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser></span><span class="sxs-lookup"><span data-stu-id="d5d73-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="d5d73-148">Örnek, denetimin <xref:System.Windows.Forms.Button> belirli özellik değerlerini yalıtılmış depolamadaki bir dosyaya okumayı ve yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="d5d73-149">İşlev, `Read` uygulama başladıktan sonra `Write` çağrılır ve işlev uygulama sona ermeden önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="d5d73-150">Örnek, `Read` ve `Write` işlevleri adlı <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Button> `MainButton`bir denetim içeren bir üye olarak var gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
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
  
## <a name="database-access"></a><span data-ttu-id="d5d73-151">Veritabanı Erişimi</span><span class="sxs-lookup"><span data-stu-id="d5d73-151">Database Access</span></span>  
 <span data-ttu-id="d5d73-152">Veritabanına erişmek için gereken izinler veritabanı sağlayıcısına göre değişir; ancak, yalnızca uygun izinlerle çalışan uygulamalar bir veritabanına veri bağlantısı üzerinden erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="d5d73-153">Veritabanına erişmek için gereken izinler hakkında daha fazla bilgi için [Kod Erişim Güvenliği ve ADO.NET](../data/adonet/code-access-security.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="d5d73-154">Uygulamanızın kısmi güven içinde çalışmasını istediğiniz için bir veritabanına doğrudan erişemiyorsanız, verilerinize erişmek için alternatif bir araç olarak bir Web hizmeti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5d73-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="d5d73-155">Web hizmeti, bir ağ üzerinden programlanabilir bir yazılım dır.</span><span class="sxs-lookup"><span data-stu-id="d5d73-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="d5d73-156">Web hizmetleriyle, uygulamalar verileri kod grubu bölgeleri arasında paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="d5d73-157">Varsayılan olarak, yerel intranet ve Internet bölgelerindeki uygulamalara, aynı sunucuda barındırılan bir Web hizmetini aramalarına olanak tanıyan başlangıç sitelerine erişme hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="d5d73-158">Daha fazla bilgi için ASP.NET AJAX veya [Windows Communication Foundation](../wcf/index.md)web [hizmetlerine](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) bakın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="d5d73-159">Kayıt Defteri Erişimi</span><span class="sxs-lookup"><span data-stu-id="d5d73-159">Registry Access</span></span>  
 <span data-ttu-id="d5d73-160">Sınıf, <xref:System.Security.Permissions.RegistryPermission> işletim sistemi kayıt defterine erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="d5d73-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="d5d73-161">Varsayılan olarak, yalnızca yerel olarak çalışan uygulamalar kayıt defterine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="d5d73-162"><xref:System.Security.Permissions.RegistryPermission>yalnızca bir uygulamaya kayıt defterierişimini deneme hakkı verir; işletim sistemi kayıt defterinde güvenliği hala zorladığı için erişimin başarılı olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="d5d73-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="d5d73-163">Kayıt defterine kısmi güven altında erişemediğiniz için, verilerinizi depolamak için başka yöntemler bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="d5d73-164">Uygulama ayarlarını depolarken, kayıt defteri yerine yalıtılmış depolama yı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5d73-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="d5d73-165">Yalıtılmış depolama, uygulamaya özgü diğer dosyaları depolamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5d73-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="d5d73-166">Varsayılan olarak bir uygulamaya sitenin menşei olan siteye erişim hakkı verildiğinden, sunucu veya kaynak site hakkında genel uygulama bilgilerini de depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5d73-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d73-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d73-167">See also</span></span>

- [<span data-ttu-id="d5d73-168">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="d5d73-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="d5d73-169">Windows Forms'ta Ek Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="d5d73-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="d5d73-170">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d5d73-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="d5d73-171">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d5d73-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="d5d73-172">Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="d5d73-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="d5d73-173">MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)</span><span class="sxs-lookup"><span data-stu-id="d5d73-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
