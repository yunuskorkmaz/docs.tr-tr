---
title: Yönetilmeyen uygulamalara genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: 0b4c3e738848be1ead2adeb1945e168c9db60071
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732527"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış
Windows Forms uygulamalar ve denetimler, bazı uyarılarla yönetilmeyen uygulamalarla birlikte çalışabilir. Aşağıdaki bölümlerde, uygulamaları ve denetimleri Windows Forms uygulamalar ve denetimlerin desteklediği senaryolar ve Konfigürasyonlar açıklanır.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Forms denetimleri ve ActiveX uygulamaları  
 Microsoft Internet Explorer ve Microsoft Foundation Sınıfları (MFC) dışında, ActiveX denetimlerini barındırmak için tasarlanan uygulamalarda Windows Forms denetimleri desteklenmez. Visual Studio .NET 2003 ' den önceki Visual Studio sürümlerinden ActiveX test kapsayıcıları dahil olmak üzere, ActiveX denetimlerini barındırabilen diğer uygulamalar ve geliştirme araçları Windows Forms denetimleri için desteklenen konaklar değildir.  
  
 Bu kısıtlamalar, bileşen nesne modeli COM birlikte çalışabilirliği aracılığıyla Windows Forms denetimlerinin kullanımı için de geçerlidir. COM çağrılabilir sarmalayıcı (CCW) aracılığıyla Windows Forms denetiminin kullanılması yalnızca Internet Explorer 'da desteklenir. COM birlikte çalışma hakkında daha fazla bilgi için bkz.  
  
 [Com birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 Aşağıdaki tabloda Windows Forms denetimleri için kullanılabilir ActiveX barındırma desteği gösterilmektedir.  
  
|Windows Forms sürümü|Destek|  
|---------------------------|-------------|  
|.NET Framework sürüm 1,0|Internet Explorer 5,01 ve sonraki sürümleri|  
|.NET Framework sürüm 1,1 ve üzeri|Internet Explorer 5,01 ve sonraki sürümleri<br /><br /> Microsoft Foundation Sınıfları (MFC) 7,0 ve üzeri|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Bileşenleri ActiveX denetimleri olarak barındırma Windows Forms  
 .NET Framework 1,1 ' de, destek MFC 7,0 ve sonraki sürümleri içerecek şekilde genişletildi. Bu destek MFC 7,0 ve sonraki ActiveX denetim kapsayıcısıyla tam uyumlu olan tüm kapsayıcıları içerir.  
  
 Ancak, Windows Forms denetimlerinin ActiveX denetimleri olarak kaydı desteklenmez. Ayrıca, Windows Forms denetimleri için `com.ms.win32.Ole32.CoCreateInstance` yöntemi çağrılması desteklenmez. Yalnızca Windows Forms denetimlerinin yönetilen etkinleştirmesi desteklenir. Bir Windows Forms denetimi oluşturduktan sonra, bunu bir MFC uygulamasında bir ActiveX denetimiyle olduğu gibi barındırabilirsiniz.  
  
 Yönetilmeyen uygulamanızda Windows Forms denetimleri kullanmak için, yönetilmeyen CLR barındırma API 'Lerini kullanarak CLR 'yi barındırmalısınız ya da C++ birlikte çalışma özelliklerini kullanmanız gerekir. C++ Birlikte çalışabilirlik özelliklerinin kullanılması önerilen çözümdür.  
  
## <a name="windows-forms-in-com-client-applications"></a>COM istemci uygulamalarında Windows Forms  
 Visual Basic 6,0 uygulaması veya MFC uygulaması gibi bir COM istemci uygulamasından bir Windows formunu açtığınızda form beklenmedik şekilde davranabilir. Örneğin, sekme tuşuna bastığınızda, odak bir denetimden başka bir denetime değişmez. Komut düğmesi odağa sahip olduğunda ENTER tuşuna bastığınızda, düğmenin <xref:System.Windows.Forms.Control.Click> olayı oluşturulmaz. Ayrıca, tuş vuruşları veya fare etkinlikleri için beklenmeyen davranışlara da karşılaşabilirsiniz.  
  
 Bu davranış, yönetilmeyen uygulama Windows Forms doğru çalışması gereken ileti döngüsü desteğini uygulamadığı için oluşur. COM istemci uygulaması tarafından sunulan ileti döngüsü Windows Forms ileti döngüsünden temelde farklıdır.  
  
 Bir uygulamanın ileti döngüsü, bir iş parçacığının ileti kuyruğundan iletileri alan, bunları çeviren ve sonra işlenecek uygulamaya gönderen bir iç program döngüsüdür. Bir Windows formu için ileti döngüsü, daha önceki uygulamaların yanı sıra Visual Basic 6,0 uygulamaları ve MFC uygulamaları gibi, ileti döngüsüyle aynı mimariye sahip değildir. İleti döngüsüne gönderilen pencere iletileri, Windows form 'un beklediği şekilde farklı şekilde işlenebilir. Bu nedenle, beklenmeyen davranış ortaya çıkabilir. Bazı tuş vuruşu birleşimleri çalışmayabilir, bazı fare etkinlikleri çalışmayabilir veya bazı olaylar beklendiği gibi görüntülenmeyebilir.  
  
## <a name="resolving-interoperability-issues"></a>Birlikte çalışabilirlik sorunlarını çözme  
 Bu sorunları, <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi kullanılarak oluşturulan .NET Framework ileti döngüsünde formu görüntüleyerek çözebilirsiniz.  
  
 Bir Windows formunun bir COM istemci uygulamasından düzgün çalışmasını sağlamak için, bunu bir Windows Forms ileti döngüsünde çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
- Windows formunu göstermek için <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek com birlikte çalışmasını destekleme](com-interop-by-displaying-a-windows-form-shadow.md).  
  
- Her Windows formunu yeni bir iş parçacığında görüntüleyin. Daha fazla bilgi için, bkz. [nasıl yapılır: her Windows formunu kendi Iş parçacığında görüntüleyerek com birlikte çalışmasını destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms ve Yönetilmeyen Uygulamalar](windows-forms-and-unmanaged-applications.md)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [COM birlikte çalışabilirlik örnekleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/cxcz83xf(v=vs.90))
- [Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)
- [.NET Framework Bileşenlerini COM'da Gösterme](../../interop/exposing-dotnet-components-to-com.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../interop/packaging-an-assembly-for-com.md)
- [Bütünleştirilmiş Kodları COM ile Kaydetme](../../interop/registering-assemblies-with-com.md)
- [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](com-interop-by-displaying-a-windows-form-shadow.md)
- [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
