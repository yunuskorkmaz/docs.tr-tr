---
title: Windows Forms'ta Ek Güvenlik Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: 6ab7b4d8fe8366a214d70cd73e7e33cafcc584f8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409399"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows Forms'ta Ek Güvenlik Konuları
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] güvenlik ayarları, uygulamanızın farklı bir kısmi güven ortamında yerel bilgisayarınızda çalıştırılmasına neden olabilir. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Dosya sistemi, ağ ve diğer özelliklerin yanı sıra yönetilmeyen API gibi önemli yerel kaynaklara erişimi kısıtlar. Güvenlik ayarları, Microsoft Windows API veya güvenlik sistemi tarafından doğrulanan diğer API'lerini çağırma özelliği etkiler. Güvenlik dahil dosya ve veri erişimini ve yazdırma uygulamanızın diğer yönlerini de etkiler. Kısmi güven ortamında dosya ve veri erişimi hakkında daha fazla bilgi için bkz. [daha fazla güvenli dosya ve veri erişimi Windows Forms'ta](more-secure-file-and-data-access-in-windows-forms.md). Kısmi güven ortamında yazdırma hakkında daha fazla bilgi için bkz. [daha güvenli yazdırma Windows Forms'ta](more-secure-printing-in-windows-forms.md).  
  
 Aşağıdaki bölümlerde, panoyla çalışma, pencere işleyin ve kısmi güven ortamında çalışan uygulamalardan Windows API çağırmak nasıl açıklanmaktadır.  
  
## <a name="clipboard-access"></a>Pano erişim  
 <xref:System.Security.Permissions.UIPermission> Sınıfı Pano ve ilişkili erişimi denetleyen <xref:System.Security.Permissions.UIPermissionClipboard> sabit listesi değeri erişim düzeyini gösterir. Aşağıdaki tablo olası izin düzeylerini gösterir.  
  
|UIPermissionClipboard değeri|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Pano, kısıtlama kullanılabilir.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Pano bazı sınırlamalarla birlikte kullanılabilir. Verileri Pano'ya (Kopyala veya Kes komutu işlemi) yerleştirme olanağı kısıtlanır. Pano verilerini yapıştırma, bir metin kutusu gibi kabul iç denetimleri kabul edebilir, ancak kullanıcı denetimleri programlama yoluyla Pano okunamıyor.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Pano kullanılamaz.|  
  
 Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> erişim ve Internet bölgesi alan <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> erişim. Bu uygulamayı panoya kopyalayabilir, ancak uygulama program aracılığıyla için yapıştırın veya panodan okuma anlamına gelir. Bu kısıtlamalar, başka bir uygulama tarafından panoya kopyalandı programların dosyasından okurken içerik tam güven olmadan engelleyin. Uygulamanızın tam Pano erişimi gerektirir, ancak izinlere sahip değilsiniz, uygulamanız için izinler yükseltmesine gerekecektir. Yükseltme yaptığınıza izinler hakkında daha fazla bilgi için bkz. [Genel Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Pencere işleme  
 <xref:System.Security.Permissions.UIPermission> Sınıfı da pencere işleme ve diğer kullanıcı Arabirimi ile ilgili eylemler ve ilişkili gerçekleştirme izni denetler <xref:System.Security.Permissions.UIPermissionWindow> sabit listesi değeri erişim düzeyini gösterir. Aşağıdaki tablo olası izin düzeylerini gösterir.  
  
 Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> erişim ve Internet bölgesi alan <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> erişim. Bu Internet bölgesinde uygulama çoğu Pencereleme ve UI eylemlerini gerçekleştirebilirsiniz, ancak pencerenin görünümü değiştirilecek anlamına gelir. Değiştirilen pencere ilk kez çalıştırdığınızda bir balon bildirim görüntüler, değiştirilen başlık çubuğu metni içerir ve başlık çubuğunda bir Kapat düğmesi gerektirir. Uygulama, kısmi güven altında çalışan uygulamanın kullanıcı balon bildirim ve başlık çubuğunu tanımlayın.  
  
|UIPermissionWindow değeri|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Kullanıcılar, tüm windows ve kısıtlama olmaksızın kullanıcı girdi olaylarını kullanabilir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Kullanıcılar, çizim için yalnızca güvenli üst düzey pencereler ve güvenli bir alt düzey pencereleri kullanabilirsiniz ve bu üst düzey pencereler ve alt düzey pencereleri içinde kullanıcı arabirimi için yalnızca kullanıcı girdi olaylarını kullanabilirsiniz. Bu daha güvenli bir windows açıkça etiketlenmiş ve minimum ve maksimum boyutu kısıtlamaları yoktur. Kısıtlamaları sistem oturum açma ekranlarını veya sistem Masaüstü taklidi yaparak, herhangi gibi zararlı sahtekarlık saldırılarını önler ve programlı erişim, windows ve odak ile ilgili API'ler kullanımı üst sınırlar <xref:System.Windows.Forms.ToolTip> denetimi|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Kullanıcılar yalnızca güvenli bir alt düzey pencereleri çizim için kullanabilir ve yalnızca kullanıcı giriş olayları, subwindow içinde kullanıcı arabirimi için kullanabilirsiniz. Tarayıcıda görüntülenen bir denetim, güvenli subwindow örneğidir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Kullanıcılar, herhangi bir windows veya kullanıcı arabirimi olaylarının kullanamaz. Kullanıcı arabirimi olmadan kullanılabilir.|  
  
 Tarafından tanımlanan her bir izin düzeyi <xref:System.Security.Permissions.UIPermissionWindow> numaralandırma üstlerindeki daha az Eylemler sağlar. Aşağıdaki tablolarda tarafından kısıtlanmış eylemleri belirtmek <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> ve <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> değerleri. Her üye için gerekli olan tam izinleri için .NET Framework sınıf kitaplığı belgelerindeki bu üye için bkz.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> Aşağıdaki tabloda listelenen eylemleri izin önler.  
  
|Bileşen|Kısıtlı eylemleri|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Ayarlama <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> özelliği.|  
|<xref:System.Windows.Forms.Control>|-Başlarken <xref:System.Windows.Forms.Control.Parent%2A> özelliği.<br />-Ayarlama `Region` özelliği.<br />-Çağırma <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> ve <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, veya <xref:System.Windows.Forms.Control.SetTopLevel%2A> yöntemi.<br />-Çağırma <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> denetim döndürdüyse yöntemi çağıran denetiminin alt değil.<br />-Bir kapsayıcı denetimi içinde denetim odağı değiştirin.|  
|<xref:System.Windows.Forms.Cursor>|-Ayarlama <xref:System.Windows.Forms.Cursor.Clip%2A> özelliği.<br />-Çağırma <xref:System.Windows.Forms.Control.Hide%2A> yöntemi.|  
|<xref:System.Windows.Forms.DataGrid>|-Çağırma <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> yöntemi.|  
|<xref:System.Windows.Forms.Form>|-Başlarken <xref:System.Windows.Forms.Form.ActiveForm%2A> veya <xref:System.Windows.Forms.Form.MdiParent%2A> özelliği.<br />-Ayarlama <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, veya <xref:System.Windows.Forms.Form.TopMost%2A> özelliği.<br />-Ayarlama <xref:System.Windows.Forms.Form.Opacity%2A> % 50 aşağıda özelliği.<br />-Ayarlama <xref:System.Windows.Forms.Form.WindowState%2A> özelliğini <xref:System.Windows.Forms.FormWindowState.Minimized> programlı olarak.<br />-Çağırma <xref:System.Windows.Forms.Form.Activate%2A> yöntemi.<br />-Kullanarak <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, ve <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> sabit listesi değerleri.|  
|<xref:System.Windows.Forms.NotifyIcon>|-Kullanarak <xref:System.Windows.Forms.NotifyIcon> bileşen tamamen kısıtlıdır.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Değeri sınırlar aşağıdaki tabloda, tarafından uygulanan kısıtlamalara ek olarak listelenen eylemleri <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> değeri.  
  
|Bileşen|Kısıtlı eylemleri|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Gösteren bir iletişim kutusu türetilen <xref:System.Windows.Forms.CommonDialog> sınıfı.|  
|<xref:System.Windows.Forms.Control>|-Çağırma <xref:System.Windows.Forms.Control.CreateGraphics%2A> yöntemi.<br />-Ayarlama <xref:System.Windows.Forms.Control.Cursor%2A> özelliği.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Ayarlama <xref:System.Windows.Forms.Cursor.Current%2A> özelliği.|  
|<xref:System.Windows.Forms.MessageBox>|-Çağırma <xref:System.Windows.Forms.Form.Show%2A> yöntemi.|  
  
### <a name="hosting-third-party-controls"></a>Üçüncü taraf denetimleri barındırma  
 Farklı türde bir pencere işleme formlarınızı üçüncü taraf denetimleri ana ortaya çıkabilir. Herhangi bir özel bir üçüncü taraf denetimdir <xref:System.Windows.Forms.UserControl> geliştirilen ve kendiniz derlenmiş olduğunuz değil. Barındırma senaryo yararlanma zor olsa da, teorik olarak bir üçüncü taraf denetimi tüm alan formunuzun kapsayacak şekilde, işleme yüzeyini genişletmek mümkündür. Bu denetim kritik iletişim kutusu taklit sonra kullanıcı adı/parola birleşimleri veya banka hesabı numarası gibi bilgileri kullanıcılarınızdan gelen istek.  
  
 Bu riski sınırlamak için güvenebileceğiniz satıcılardan yalnızca üçüncü taraf denetimleri kullanın. Üçüncü taraf denetimleri doğrulanamayan bir kaynaktan yüklediğiniz kullanırsanız, olası davranışları için kaynak kodu gözden geçirmenizi öneririz. Kaynak kötü amaçlı olmayan olduğunu doğruladıktan sonra derleme derlemelisiniz kendinize kaynak derleme eşleştiğinden emin olun.  
  
## <a name="windows-api-calls"></a>Windows API çağrıları  
 Uygulama tasarımınızı Windows API'SİNDEN bir işlev çağırmanın gerektiriyorsa, yönetilmeyen kod erişiyor. Bu durumda, Windows API çağrıları veya değerleri ile çalışırken kodun eylemleri pencere veya işletim sistemi belirlenemiyor. <xref:System.Security.Permissions.SecurityPermission> Sınıfı ve <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> değerini <xref:System.Security.Permissions.SecurityPermissionFlag> numaralandırma yönetilmeyen kod erişimi denetleme. Yalnızca verildiğinde uygulamanın yönetilmeyen koda erişebilirsiniz <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni. Varsayılan olarak, yerel olarak çalıştırıyorsanız, yalnızca uygulamaları yönetilmeyen kodu çağırabilir.  
  
 Windows Forms bazı gerektiren yönetilmeyen erişmeyi <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni. Aşağıdaki tabloda üyeleri listeler <xref:System.Windows.Forms> iznin gerekli ad alanı. .NET Framework sınıf kitaplığı belgelerindeki bir üye için gerekli olan izinler hakkında daha fazla bilgi için bkz.  
  
|Bileşen|Üye|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> Yöntemi<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Özelliği<br />-   `Exit` Yöntemi<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> Yöntemi<br />-   <xref:System.Windows.Forms.Application.ThreadException> Olay|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> Yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> Yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> Yöntemi|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> Yöntemi<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> Yöntemi<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> Yöntemi<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> Yöntemi|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Yöntemleri<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> Yöntemi|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> Sınıfı|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> Yöntemi|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> Yöntemi<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> Yöntemi|  
  
 Uygulamanızı yönetilmeyen kodu çağırma izni yoksa, uygulamanızın istemelisiniz <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni veya özelliklerini uygulama alternatif yolu düşünmeniz gerekir; çoğu durumda, Windows Forms Windows yönetilen bir alternatif sağlar. API işlevleri. Mevcut olmadığı anlamına gelir ve uygulamanın yönetilmeyen kod erişmeniz gerekiyorsa uygulama izinlerini yükseltmesine gerekecektir.  
  
 Yönetilmeyen kod çağırmak için izin en herhangi bir şey gerçekleştirmek uygulamaya izin verir. Bu nedenle, yönetilmeyen kod çağırmak için izin güvenilir bir kaynaktan gelen uygulamaların yalnızca verilmelidir. Alternatif olarak, uygulamaya bağlı olarak, isteğe bağlı ya da yalnızca tam güven ortamında etkin yönetilmeyen koda çağrı yapan uygulamanın işlevsellik parçası olabilir. Tehlikeli izinler hakkında daha fazla bilgi için bkz: [tehlikeli izinler ve ilke yönetimi](../misc/dangerous-permissions-and-policy-administration.md). Yükseltme yaptığınıza izinler hakkında daha fazla bilgi için bkz. [Genel Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms'ta Daha Güvenli Yazdırma](more-secure-printing-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
- [ClickOnce Uygulamalarının Güvenliğini Sağlama](/visualstudio/deployment/securing-clickonce-applications)
