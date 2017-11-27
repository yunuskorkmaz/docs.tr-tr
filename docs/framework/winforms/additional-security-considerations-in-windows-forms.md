---
title: "Windows Forms'ta Ek Güvenlik Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b8b693f7faf9abb71d214ca755fc9587a1dcc0ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows Forms'ta Ek Güvenlik Konuları
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]güvenlik ayarları uygulamanız farklı bir kısmi güven ortamında yerel bilgisayarınızda çalışmasına neden olabilir. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Dosya sistemi, ağ ve başka şeylerin yönetilmeyen API'ler kritik gibi yerel kaynaklara erişimi kısıtlar. Güvenlik ayarları Microsoft Win32 API veya diğer güvenlik sistemi tarafından doğrulanıp doğrulanamadığını API'larını çağırma yeteneği etkiler. Güvenlik, dosya ve veri erişim dahil olmak üzere ve yazdırma uygulamanızın diğer yönlerini de etkiler. Kısmi güven ortamında dosya ve veri erişim hakkında daha fazla bilgi için bkz: [daha fazla güvenli dosya ve Windows Forms veri erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md). Kısmi güven ortamında yazdırma hakkında daha fazla bilgi için bkz: [daha fazla Güvenli Yazdırma Windows Forms'ta](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md).  
  
 Aşağıdaki bölümlerde nasıl Pano ile çalışır, pencere değişikliği gerçekleştiren ve bir kısmi güven ortamında çalışan uygulamalardan Win32 API çağrısı açıklanmaktadır.  
  
## <a name="clipboard-access"></a>Pano erişim  
 <xref:System.Security.Permissions.UIPermission> Sınıfı Pano ve ilişkili erişimi kontrol <xref:System.Security.Permissions.UIPermissionClipboard> numaralandırma değeri erişim düzeyini belirtir. Aşağıdaki tabloda olası izin düzeyleri gösterilmektedir.  
  
|UIPermissionClipboard değeri|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Pano, kısıtlama kullanılabilir.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Pano bazı kısıtlamalar ile kullanılabilir. Veri (kopyalama veya kesme komutu işlemleri) Pano'ya yerleştir olanağı kısıtlanır. Pano verilerini yapıştırma gibi bir metin kutusu kabul iç denetimleri kabul edebilir, ancak kullanıcı denetimlerini programlı olarak panodan okunamıyor.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Pano kullanılamaz.|  
  
 Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> erişim ve Internet bölgesi alan <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> erişim. Bu uygulamanın veri panoya kopyalayabilirsiniz, ancak uygulama olamaz program aracılığıyla için yapıştırın veya panodan okuma anlamına gelir. Bu kısıtlamalar başka bir uygulama tarafından panoya kopyalandı programların okuma içerik tam güven olmadan engelleyin. Uygulamanızı tam Pano erişimi gerektirir, ancak izinlere sahip değil, uygulamanızın izinlerini yükseltmesine gerekecektir. Yükseltme yaptığınıza izinleri hakkında daha fazla bilgi için bkz: [Genel Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="window-manipulation"></a>Pencere işleme  
 <xref:System.Security.Permissions.UIPermission> Sınıfı ayrıca penceresi işleme ve diğer kullanıcı Arabirimi ile ilgili eylemler ve ilişkili gerçekleştirme izni denetler <xref:System.Security.Permissions.UIPermissionWindow> numaralandırma değeri erişim düzeyini belirtir. Aşağıdaki tabloda olası izin düzeyleri gösterilmektedir.  
  
 Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> erişim ve Internet bölgesi alan <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> erişim. Bu'nin Internet bölgesinde uygulama çoğu Pencereleme ve UI eylemlerini gerçekleştirebilir, ancak pencerenin görünümü değiştirilecek anlamına gelir. Değiştirilen penceresi ilk kez çalıştırdığınızda balon bildirim görüntüler, değiştirilmiş başlık çubuğu metni içerir ve Kapat düğmesini başlık çubuğunda gerektirir. Balon bildirim ve başlık çubuğu uygulama kısmi güven altında çalıştığı uygulama kullanıcı için belirleyin.  
  
|UIPermissionWindow değeri|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Kullanıcılar, tüm windows ve kullanıcı girdi olaylarını kısıtlama olmaksızın kullanabilir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Kullanıcılar yalnızca güvenli en üst düzey windows ve daha güvenli subwindows çizim için kullanabilir ve yalnızca kullanıcı giriş olaylarını bu üst düzey windows ve subwindows içinde kullanıcı arabirimi için kullanabilirsiniz. Bu daha güvenli windows açıkça etiketlenir ve minimum ve maksimum boyut kısıtlamaları vardır. Sistem oturum açma ekranlarını veya sistem Masaüstü taklidi yaparak, herhangi gibi zararlı sahtekarlık saldırılarını önler ve windows, odak ilgili API'ler ve kullanımını üst öğeye programlı erişimi kısıtlayan kısıtlama <xref:System.Windows.Forms.ToolTip> denetimi|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Kullanıcılar yalnızca güvenli subwindows çizim için kullanabilir ve yalnızca kullanıcı giriş olaylarını bu subwindow içinde kullanıcı arabirimi için kullanabilirsiniz. Bir tarayıcı içinde görüntülenen bir denetim, daha güvenli bir subwindow örneğidir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Kullanıcılar, herhangi bir windows veya kullanıcı arabirimi olayları kullanamaz. Kullanıcı arabirimi olmadan kullanılabilir.|  
  
 Tarafından tanımlanan her izin düzeyi <xref:System.Security.Permissions.UIPermissionWindow> numaralandırma, yukarıdaki düzey daha az Eylemler sağlar. Aşağıdaki tablolarda tarafından kısıtlanan eylemleri gösteren <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> ve <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> değerleri. Her üye için gerekli olan tam izinleri için bu üye .NET Framework sınıf kitaplığı belgeleri için bkz.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>Aşağıdaki tabloda listelenen eylemler izni kısıtlar.  
  
|Bileşen|Kısıtlı Eylemler|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Ayar <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> özelliği.|  
|<xref:System.Windows.Forms.Control>|-Alma <xref:System.Windows.Forms.Control.Parent%2A> özelliği.<br />-Ayar `Region` özelliği.<br />-Çağırma <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> ve <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, veya <xref:System.Windows.Forms.Control.SetTopLevel%2A> yöntemi.<br />-Çağırma <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> denetimi döndürülürse yöntemi çağırma denetim alt değil.<br />-Denetim odağı bir kapsayıcı denetiminin içinde değiştirin.|  
|<xref:System.Windows.Forms.Cursor>|-Ayar <xref:System.Windows.Forms.Cursor.Clip%2A> özelliği.<br />-Çağırma <xref:System.Windows.Forms.Control.Hide%2A> yöntemi.|  
|<xref:System.Windows.Forms.DataGrid>|-Çağırma <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> yöntemi.|  
|<xref:System.Windows.Forms.Form>|-Alma <xref:System.Windows.Forms.Form.ActiveForm%2A> veya <xref:System.Windows.Forms.Form.MdiParent%2A> özelliği.<br />-Ayar <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, veya <xref:System.Windows.Forms.Form.TopMost%2A> özelliği.<br />-Ayar <xref:System.Windows.Forms.Form.Opacity%2A> % 50 aşağıda özelliği.<br />-Ayar <xref:System.Windows.Forms.Form.WindowState%2A> özelliğine <xref:System.Windows.Forms.FormWindowState.Minimized> programlı olarak.<br />-Çağırma <xref:System.Windows.Forms.Form.Activate%2A> yöntemi.<br />-Kullanma <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, ve <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> numaralandırma değerleri.|  
|<xref:System.Windows.Forms.NotifyIcon>|-Kullanma <xref:System.Windows.Forms.NotifyIcon> bileşeni tamamen kısıtlıdır.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Değeri sınırlar tarafından yerleştirilen kısıtlamaları ek olarak aşağıdaki tabloda listelenen eylemleri <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> değeri.  
  
|Bileşen|Kısıtlı Eylemler|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Bir iletişim kutusu gösteren türetilen <xref:System.Windows.Forms.CommonDialog> sınıfı.|  
|<xref:System.Windows.Forms.Control>|-Çağırma <xref:System.Windows.Forms.Control.CreateGraphics%2A> yöntemi.<br />-Ayar <xref:System.Windows.Forms.Control.Cursor%2A> özelliği.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Ayar <xref:System.Windows.Forms.Cursor.Current%2A> özelliği.|  
|<xref:System.Windows.Forms.MessageBox>|-Çağırma <xref:System.Windows.Forms.Form.Show%2A> yöntemi.|  
  
### <a name="hosting-third-party-controls"></a>Üçüncü taraf denetimleri barındırma  
 Üçüncü taraf denetimleri formlarınızı konak penceresi işleme başka bir tür oluşabilir. Herhangi bir özel bir üçüncü taraf denetimdir <xref:System.Windows.Forms.UserControl> geliştirilen ve kendiniz derlenmiş olduğunuz değil. Barındırma senaryo yararlanmaya sabit olsa da, teorik olarak, formun tüm alanını kaplamak için kendi işleme yüzeyi genişletmek üçüncü taraf denetimi için mümkündür. Bu denetim sonra bir kritik iletişim kutusu taklit etmek ve kullanıcı adı/parola birleşimleri veya banka hesap numaraları gibi bilgileri, kullanıcılardan isteyin.  
  
 Bu riski sınırlamak için yalnızca güvenilir satıcılardan üçüncü taraf denetimleri kullanın. Üçüncü taraf denetimleri doğrulanamayan bir kaynaktan indirmiş kullanırsanız, olası açıkları için kaynak kodunu gözden geçirmenizi öneririz. Kaynak kötü amaçlı olmayan olduğunu doğruladıktan sonra derleme derleme kendinize kaynak assembly eşleştiğinden emin olun.  
  
## <a name="win32-api-calls"></a>Win32 API çağrıları  
 Uygulama tasarımı Win32 API öğesinden bir işlevi çağırmak gerektiriyorsa, yönetilmeyen kod erişiyorsunuz. Bu durumda, Win32 API çağrıları veya değerleri ile çalışırken kodun Eylemler pencere veya işletim sistemi belirlenemiyor. <xref:System.Security.Permissions.SecurityPermission> Sınıfı ve <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> değerini <xref:System.Security.Permissions.SecurityPermissionFlag> numaralandırma yönetilmeyen kod erişimi denetleme. Yalnızca verildiğinde uygulamanın yönetilmeyen kod erişebilirsiniz <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni. Varsayılan olarak, yerel olarak çalışan yalnızca uygulamaları yönetilmeyen kod çağırabilir.  
  
 Bazı Windows Forms üyeleri gerektiren yönetilmeyen erişebilmesi <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni. Aşağıdaki tabloda yer alan üyelerin listeler <xref:System.Windows.Forms> izni gerektiren ad alanı. Bir üye için gerekli olan izinler hakkında daha fazla bilgi için .NET Framework sınıf kitaplığı belgelerine bakın.  
  
|Bileşen|Üye|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A>yöntemi<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A>özelliği<br />-   `Exit`yöntemi<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A>yöntemi<br />-   <xref:System.Windows.Forms.Application.ThreadException>Olay|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A>yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A>yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>yöntemi|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A>yöntemi<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A>yöntemi<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A>yöntemi<br />-   <xref:System.Windows.Forms.Control.WndProc%2A>yöntemi|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A>yöntemleri<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>yöntemi|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow>sınıfı|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A>yöntemi|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A>yöntemi<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A>yöntemi|  
  
 Uygulamanızı yönetilmeyen kodu çağırma izni yoksa, uygulamanız istemelidir <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni veya özelliklerini uygulama alternatif yöntemler düşünmeniz gerekir; çoğu durumda, Windows Forms Win32 API yönetilen bir alternatif sunar. İşlevler. Mevcut hiçbir alternatif anlamına gelir ve uygulama yönetilmeyen kod erişmeniz gerekiyorsa, uygulama izinlerini yükseltmesine gerekecektir.  
  
 Yönetilmeyen kodu çağırma izni en herhangi bir şey gerçekleştirmek bir uygulama sağlar. Bu nedenle, yönetilmeyen kodu çağırma izni yalnızca güvenilen bir kaynaktan geliyor uygulamalar için verilmiş olmalıdır. Alternatif olarak, uygulamaya bağlı olarak, isteğe bağlı ya da yalnızca tam güven ortamında etkin yönetilmeyen koda çağrı yaparsa uygulama işlevselliği parçası olabilir. Tehlikeli izinler hakkında daha fazla bilgi için bkz: [tehlikeli izinler ve ilke yönetimi](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md). Yükseltme yaptığınıza izinleri hakkında daha fazla bilgi için bkz: [NIB: Genel Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Daha güvenli dosya ve Windows Forms veri erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Windows Forms'ta daha güvenli yazdırma](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Windows Forms'a genel bakış güvenliği](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms güvenliği](../../../docs/framework/winforms/windows-forms-security.md)  
 [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications)
