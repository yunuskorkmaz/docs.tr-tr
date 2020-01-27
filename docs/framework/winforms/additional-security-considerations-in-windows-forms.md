---
title: Ek güvenlik konuları
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739814"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows Forms'ta Ek Güvenlik Konuları
.NET Framework güvenlik ayarları, uygulamanızın bir kısmi güven ortamında yerel bilgisayarınızdan farklı şekilde çalışmasına neden olabilir. .NET Framework, diğer şeyler arasında dosya sistemi, ağ ve yönetilmeyen API 'Ler gibi bu kritik yerel kaynaklara erişimi kısıtlar. Güvenlik ayarları, Microsoft Windows API 'sini veya güvenlik sistemi tarafından doğrulanamayan diğer API 'Leri çağırma yeteneğini etkiler. Güvenlik Ayrıca, dosya ve veri erişimi ve yazdırma dahil olmak üzere uygulamanızın diğer yönlerini de etkiler. Kısmi güven ortamındaki dosya ve veri erişimi hakkında daha fazla bilgi için, bkz. [Windows Forms daha güvenli dosya ve veri erişimi](more-secure-file-and-data-access-in-windows-forms.md). Kısmi güven ortamında yazdırma hakkında daha fazla bilgi için, [Windows Forms daha güvenli yazdırma](more-secure-printing-in-windows-forms.md)bölümüne bakın.  
  
 Aşağıdaki bölümlerde, pano ile çalışmayı, pencere düzenlemesini gerçekleştirmeyi ve kısmi güven ortamında çalışan uygulamalardan Windows API 'sini çağırma ele alınmaktadır.  
  
## <a name="clipboard-access"></a>Pano erişimi  
 <xref:System.Security.Permissions.UIPermission> sınıfı panoya erişimi denetler ve ilişkili <xref:System.Security.Permissions.UIPermissionClipboard> numaralandırma değeri erişim düzeyini gösterir. Aşağıdaki tabloda olası izin düzeyleri gösterilmektedir.  
  
|UIPermissionClipboard değeri|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Pano, kısıtlama olmadan kullanılabilir.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Pano bazı kısıtlamalarla kullanılabilir. Panoya veri yerleştirme (komut işlemlerini kopyalama veya kesme) özelliği Kısıtlamasız. Metin kutusu gibi yapıştırmayı kabul eden iç denetimler Pano verilerini kabul edebilir, ancak kullanıcı denetimleri panodan program aracılığıyla okunamaz.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Pano kullanılamıyor.|  
  
 Varsayılan olarak, yerel Intranet bölgesi <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> erişim alır ve Internet bölgesi <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> erişim alır. Bu, uygulamanın panoya veri kopyalayabileceği, ancak uygulamanın Pano 'ya program aracılığıyla Yapıştırmayacağı veya Panodan okuyamayacağı anlamına gelir. Bu kısıtlamalar, başka bir uygulama tarafından panoya kopyalanmış içeriği okumaktan tam güven olmayan programları engeller. Uygulamanız tam Pano erişimi gerektiriyorsa, ancak izinleriniz yoksa, uygulamanız için izinleri yükseltme yapmanız gerekir. İzinleri yükseltme hakkında daha fazla bilgi için bkz. [Genel Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Pencere düzenleme  
 <xref:System.Security.Permissions.UIPermission> sınıfı ayrıca pencere işleme ve diğer kullanıcı arabirimi ile ilgili diğer eylemleri gerçekleştirme iznini denetler ve ilişkili <xref:System.Security.Permissions.UIPermissionWindow> numaralandırma değeri erişim düzeyini gösterir. Aşağıdaki tabloda olası izin düzeyleri gösterilmektedir.  
  
 Varsayılan olarak, yerel Intranet bölgesi <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> erişim alır ve Internet bölgesi <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> erişim alır. Bu, Internet bölgesinde, uygulamanın çoğu Pencereleme ve Kullanıcı arabirimi eylemini gerçekleştirebileceği, ancak pencerenin görünümünün değiştirildiği anlamına gelir. Değiştirilen pencere ilk çalıştırıldığında bir balon bildirimi görüntüler, değiştirilmiş başlık çubuğu metnini içerir ve başlık çubuğunda bir Kapat düğmesi gerektirir. Balon bildirimi ve başlık çubuğu, uygulamanın kısmi güven altında çalıştırdığı uygulamanın kullanıcısına göre belirlenir.  
  
|UIPermissionWindow değeri|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Kullanıcılar, kısıtlama olmadan tüm Windows ve Kullanıcı giriş olaylarını kullanabilir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Kullanıcılar çizim için yalnızca daha güvenli olan üst düzey Windows ve daha güvenli bir alt pencere kullanabilir ve yalnızca bu üst düzey Windows ve alt pencere içindeki kullanıcı arabirimi için Kullanıcı giriş olaylarını kullanabilir. Bu güvenli pencereler açıkça etiketlidir ve en düşük ve en yüksek boyut kısıtlamalarına sahiptir. Kısıtlamalar, sistem oturumu açma ekranlarını veya sistem masaüstünü taklit etmek gibi zararlı olabilecek kimlik sahtekarlığı saldırılarına engel olabilir ve üst Windows, odak ile ilgili API 'Ler ve <xref:System.Windows.Forms.ToolTip> denetimi kullanımı için programlı erişimi kısıtlar.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Kullanıcılar çizim için yalnızca daha güvenli olan alt pencereleri kullanabilir ve yalnızca o alt penceredeki Kullanıcı arabirimi için Kullanıcı giriş olaylarını kullanabilir. Bir tarayıcıda görünen denetim, daha güvenli bir alt pencerenin örneğidir.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Kullanıcılar herhangi bir Windows veya Kullanıcı arabirimi olayını kullanamaz. Kullanıcı arabirimi kullanılamaz.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow> numaralandırması tarafından tanımlanan her izin düzeyi, yukarıdaki düzeyden daha az eyleme izin verir. Aşağıdaki tablolar <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> ve <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> değerleri tarafından kısıtlanan eylemleri gösterir. Her üye için gereken tam izinler için .NET Framework Sınıf Kitaplığı belgelerindeki Bu üyeye yönelik başvuruya bakın.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> izin, aşağıdaki tabloda listelenen eylemleri kısıtlar.  
  
|Bileşen|Kısıtlanmış eylemler|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-<xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> özelliği ayarlanıyor.|  
|<xref:System.Windows.Forms.Control>|-<xref:System.Windows.Forms.Control.Parent%2A> özelliği alınıyor.<br />-`Region` özelliği ayarlanıyor.<br />-<xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> ve <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>veya <xref:System.Windows.Forms.Control.SetTopLevel%2A> yöntemi çağrılıyor.<br />-Döndürülen denetim çağıran denetimin bir alt öğesi değilse <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> yöntemi çağrılıyor.<br />-Denetimi bir kapsayıcı denetiminin içinde değiştirir.|  
|<xref:System.Windows.Forms.Cursor>|-<xref:System.Windows.Forms.Cursor.Clip%2A> özelliği ayarlanıyor.<br />-<xref:System.Windows.Forms.Control.Hide%2A> yöntemi çağrılıyor.|  
|<xref:System.Windows.Forms.DataGrid>|-<xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> yöntemi çağrılıyor.|  
|<xref:System.Windows.Forms.Form>|-<xref:System.Windows.Forms.Form.ActiveForm%2A> veya <xref:System.Windows.Forms.Form.MdiParent%2A> özelliği alınıyor.<br />-<xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>veya <xref:System.Windows.Forms.Form.TopMost%2A> özelliği ayarlanıyor.<br />-<xref:System.Windows.Forms.Form.Opacity%2A> özelliği %50 olarak ayarlanıyor.<br />-<xref:System.Windows.Forms.Form.WindowState%2A> özelliği program aracılığıyla <xref:System.Windows.Forms.FormWindowState.Minimized> olarak ayarlanıyor.<br />-<xref:System.Windows.Forms.Form.Activate%2A> yöntemi çağrılıyor.<br />-<xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>ve <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle> numaralandırma değerlerini kullanma.|  
|<xref:System.Windows.Forms.NotifyIcon>|-<xref:System.Windows.Forms.NotifyIcon> bileşeni kullanımı tamamen kısıtlıdır.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> değeri, <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> değeri tarafından verilen kısıtlamaların yanı sıra aşağıdaki tabloda listelenen eylemleri kısıtlar.  
  
|Bileşen|Kısıtlanmış eylemler|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-<xref:System.Windows.Forms.CommonDialog> sınıfından türetilmiş bir iletişim kutusu gösteriliyor.|  
|<xref:System.Windows.Forms.Control>|-<xref:System.Windows.Forms.Control.CreateGraphics%2A> yöntemi çağrılıyor.<br />-<xref:System.Windows.Forms.Control.Cursor%2A> özelliği ayarlanıyor.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-<xref:System.Windows.Forms.Cursor.Current%2A> özelliği ayarlanıyor.|  
|<xref:System.Windows.Forms.MessageBox>|-<xref:System.Windows.Forms.Form.Show%2A> yöntemi çağrılıyor.|  
  
### <a name="hosting-third-party-controls"></a>Üçüncü taraf denetimleri barındırma  
 Formlarınızın üçüncü taraf denetimlerini barındırmaları halinde başka bir pencere işleme meydana gelebilir. Üçüncü taraf denetimi, kendinizi geliştirmemiş ve derlediğiniz özel <xref:System.Windows.Forms.UserControl>. Barındırma senaryosunun yararlanması zor olsa da, üçüncü taraf bir denetim için kendi formunuzun tüm alanını kapsayacak şekilde işleme yüzeyini genişletmek için teorik olarak mümkündür. Bu denetim daha sonra kritik bir iletişim kutusunu taklit verebilir ve kullanıcılarınızın Kullanıcı adı/parola birleşimleri veya banka hesap numaraları gibi bilgileri ister.  
  
 Bu olası riski sınırlamak için, yalnızca güvenebileceğiniz satıcıların üçüncü taraf denetimlerini kullanın. Doğrulanamayan bir kaynaktan indirdiğiniz üçüncü taraf denetimleri kullanıyorsanız, olası kötüye kullanım için kaynak kodu incelemenizi öneririz. Kaynağın kötü amaçlı olmayan olduğunu doğruladıktan sonra, kaynağın derlemeyle eşleştiğinden emin olmak için derlemeyi kendiniz derlemeniz gerekir.  
  
## <a name="windows-api-calls"></a>Windows API çağrıları  
 Uygulama tasarımınız Windows API 'sinden bir işlev çağrılmasını gerektiriyorsa, yönetilmeyen koda erişiyorsunuz. Bu durumda, Windows API çağrıları veya değerleriyle çalışırken kodun pencere veya işletim sistemine yönelik eylemleri belirlenemez. <xref:System.Security.Permissions.SecurityPermission> sınıfı ve <xref:System.Security.Permissions.SecurityPermissionFlag> numaralandırmanın <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> değeri, yönetilmeyen koda erişimi denetler. Bir uygulama, yönetilmeyen koda yalnızca <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni verildiğinde erişebilir. Varsayılan olarak, yalnızca yerel olarak çalışan uygulamalar yönetilmeyen kodu çağırabilir.  
  
 Bazı Windows Forms üyeleri <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni gerektiren yönetilmeyen erişim sağlar. Aşağıdaki tabloda, izin gerektiren <xref:System.Windows.Forms> ad alanındaki üyeler listelenmektedir. Bir üye için gerekli izinler hakkında daha fazla bilgi için .NET Framework sınıf kitaplığı belgelerine bakın.  
  
|Bileşen|Üye|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemi<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> özelliği<br />-   `Exit` yöntemi<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> yöntemi<br />-   <xref:System.Windows.Forms.Application.ThreadException> olayı|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> yöntemi<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> yöntemi|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> yöntemi<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> yöntemi<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> yöntemi<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> yöntemi|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> yöntemleri<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> yöntemi|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> sınıfı|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> yöntemi|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> yöntemi<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi|  
  
 Uygulamanızın yönetilmeyen kodu çağırma izni yoksa, uygulamanızın <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> izni istemesi veya özellikleri uygulamanın alternatif yollarını dikkate almanız gerekir; birçok durumda, Windows Forms Windows API işlevlerine yönetilen bir alternatif sağlar. Başka bir yol yoksa ve uygulamanın yönetilmeyen koda erişmesi gerekiyorsa, uygulamanın izinlerini yükseltmek zorunda olursunuz.  
  
 Yönetilmeyen kodu çağırma izni bir uygulamanın birçok şeyi gerçekleştirmesine izin verir. Bu nedenle, yönetilmeyen kodu çağırma izni yalnızca güvenilir bir kaynaktan gelen uygulamalar için verilmelidir. Alternatif olarak, uygulamaya bağlı olarak, yönetilmeyen koda çağrı yapan uygulama işlevselliğinin parçası isteğe bağlı olabilir veya yalnızca tam güven ortamında etkinleştirilebilir. Tehlikeli izinler hakkında daha fazla bilgi için bkz. [tehlikeli izinler ve Ilke yönetimi](../misc/dangerous-permissions-and-policy-administration.md). İzinleri yükseltme hakkında daha fazla bilgi için bkz. [Genel Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms'ta Daha Güvenli Yazdırma](more-secure-printing-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
- [ClickOnce Uygulamalarının Güvenliğini Sağlama](/visualstudio/deployment/securing-clickonce-applications)
