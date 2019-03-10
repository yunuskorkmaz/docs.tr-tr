---
title: Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: cb7df844458be083adefa16421a7088bd1e74893
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717940"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış
Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalar ile çalışabilirler. Aşağıdaki bölümlerde, Windows Forms uygulamalarının ve denetimlerinin destekleyen ve destekledikleri değil, senaryolar ve yapılandırmaları açıklanmaktadır.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Forms denetimleri ve ActiveX uygulamalarında  
 Microsoft Internet Explorer ve Microsoft Foundation Classes (MFC) dışında Windows Forms denetimleri konak ActiveX denetimleri için tasarlanmış uygulamalar desteklenmez. Diğer uygulama ve geliştirme araçları, Visual Studio .NET 2003'ten, önceki Visual Studio sürümlerindeki ActiveX test kapsayıcılarını dahil ActiveX denetimlerini yönetiliyor Windows Forms denetimleri için desteklenen konaklar değildir.  
  
 Bu kısıtlamalar, Windows Forms denetimlerini aracılığıyla Bileşen Nesne modeli COM birlikte çalışma için de geçerlidir. COM çağrılabilir sarmalayıcı (CCW) aracılığıyla bir Windows Forms denetiminin yalnızca Internet Explorer'da desteklenir. COM birlikte çalışma hakkında daha fazla bilgi için bkz.  
  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 Aşağıdaki tabloda, Windows Forms denetimleri için desteği barındırma kullanılabilir ActiveX gösterilmektedir.  
  
|Windows Forms sürümü|Destek|  
|---------------------------|-------------|  
|.NET framework sürüm 1.0|Internet Explorer 5.01 ve sonraki sürümler|  
|.NET framework sürüm 1.1 ve üzeri|Internet Explorer 5.01 ve sonraki sürümler<br /><br /> Microsoft Foundation Classes (MFC) 7.0 ve üzeri|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Windows Forms bileşenleri ActiveX denetimleri barındırma  
 .NET Framework 1.1 desteği, MFC 7.0 ve üzeri sürümler içerecek şekilde genişletildi. Bu desteği MFC 7.0 ve üzeri ActiveX denetimi kapsayıcısı ile tamamen uyumlu olan herhangi bir kapsayıcı içerir.  
  
 Ancak, Windows Forms denetimlerinin ActiveX denetimlerini kaydı için desteklenmez. Ayrıca, çağırma `com.ms.win32.Ole32.CoCreateInstance` yöntemi Windows Forms denetimleri için desteklenmiyor. Windows Forms denetimleri için yalnızca yönetilen etkinleştirme desteklenir. Bir Windows Forms denetimi oluşturduktan sonra bunu bir MFC uygulamasında ile olduğu gibi bir ActiveX denetimini barındırabilirsiniz.  
  
 Yönetilmeyen Windows Forms denetimlerini kullanmak için yönetilmeyen CLR barındırma API'leri kullanarak CLR barındırma veya C++ birlikte çalışma özellikleri kullanın. C++ birlikte çalışabilirlik özelliklerini kullanmak önerilen çözümdür.  
  
## <a name="windows-forms-in-com-client-applications"></a>COM istemci uygulamalarının Windows Formları  
 Bir Visual Basic 6.0 uygulaması veya bir MFC uygulaması gibi bir COM istemci uygulamasından bir Windows formu açtığınızda form beklenmedik şekilde davranabilir. Örneğin, odağı TAB tuşuna bastığınızda, başka bir denetime bir denetimden değiştirmez. Bastığınızda ENTER tuşunu komut düğmesi, düğmeyi 's odaklanmışken <xref:System.Windows.Forms.Control.Click> olayı oluşmaz. Ayrıca, tuş vuruşlarınızı veya fare etkinlikleri için beklenmeyen davranışlara karşılaşabilirsiniz.  
  
 Bu davranış, yönetilmeyen Windows Forms düzgün çalışması için gereken ileti döngüsü desteği uygulamaz kaynaklanır. COM istemci uygulama tarafından sağlanan ileti döngüsü Windows Forms ileti döngüden tamamen farklıdır.  
  
 Bir uygulamanın ileti döngüsü bir iş parçacığının ileti kuyruktan iletileri alır bir program iç döngü bunları çevirir ve bunları daha sonra işlenmek üzere uygulamaya gönderir. Bir Windows formu için ileti döngüsü, Visual Basic 6.0 uygulamalarını ve MFC uygulamaları gibi eski uygulamaları sağlayan ileti döngüleri aynı mimarisine sahip değil. Windows Form beklediğinden ileti döngüsü için gönderilen pencere iletileri farklı şekilde ele alınabilir. Bu nedenle, beklenmeyen davranış oluşabilir. Bazı tuş bileşimlerini çalışmayabilir, bazı fare etkinlik çalışmayabilir veya bazı olaylar beklendiği gibi oluşturulabilir değil.  
  
## <a name="resolving-interoperability-issues"></a>Birlikte çalışabilirlik sorunlarını çözme  
 Üzerinde formunu görüntüleyerek bu sorunları çözebilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanılarak oluşturulan ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için bir Windows Forms ileti döngüsü üzerinde çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formu görüntülemek için yöntemi. Daha fazla bilgi için [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışmasını destekleme](com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Her Windows formunu yeni bir iş parçacığı üzerinde görüntüleyin. Daha fazla bilgi için [nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms ve Yönetilmeyen Uygulamalar](windows-forms-and-unmanaged-applications.md)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [COM birlikte çalışabilirlik örnekleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/cxcz83xf(v=vs.90))
- [Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)
- [.NET Framework Bileşenlerini COM'da Gösterme](../../interop/exposing-dotnet-components-to-com.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../interop/packaging-an-assembly-for-com.md)
- [Bütünleştirilmiş Kodları COM ile Kaydetme](../../interop/registering-assemblies-with-com.md)
- [Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışma desteği](com-interop-by-displaying-a-windows-form-shadow.md)
- [Nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışma desteği](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
