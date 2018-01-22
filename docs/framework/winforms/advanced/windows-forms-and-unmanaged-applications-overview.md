---
title: "Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ad64588727584a9b3de0a95e9bad252a3fb0581
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış
Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalarla birlikte çalışabilirler. Aşağıdaki bölümlerde Windows Forms uygulamaları ve denetimleri destekleyen ve değil destekleyen senaryoları ve yapılandırmaları açıklanmaktadır.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Forms denetimleri ve ActiveX uygulamaları  
 Microsoft Internet Explorer ve Microsoft Foundation sınıfları (MFC) dışında Windows Forms denetimleri konak ActiveX denetimleri için tasarlanmış uygulamaları desteklenmez. Diğer uygulamalar ve Internet Explorer'ın Visual Studio .NET 2003'ten, önceki Visual Studio sürümlerini ActiveX test kapsayıcılardan dahil olmak üzere, ActiveX denetimlerini barındırma uyumlu geliştirme araçları Windows Forms denetimleri için desteklenen ana değildir.  
  
 Bu kısıtlamaların Windows Forms denetimleri Bileşen Nesne modeli COM birlikte çalışma ile kullanım için de geçerlidir. COM aranabilir sarmalayıcısı (saat) aracılığıyla bir Windows Forms denetiminin kullanımı yalnızca Internet Explorer'da desteklenir. COM birlikte çalışma hakkında daha fazla bilgi için bkz:  
  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 Aşağıdaki tabloda Windows Forms denetimleri için destek barındırma kullanılabilir ActiveX gösterir.  
  
|Windows Forms sürümü|Destek|  
|---------------------------|-------------|  
|.NET framework sürüm 1.0|Internet Explorer 5.01 ve sonraki sürümler|  
|.NET framework sürüm 1.1 ve üzeri|Internet Explorer 5.01 ve sonraki sürümler<br /><br /> Microsoft Foundation sınıfları (MFC) 7.0 ve üzeri|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Windows Forms bileşenleri ActiveX denetimlerini barındırma  
 .NET Framework 1.1 desteği, MFC 7.0 ve sonraki sürümleri dahil olmak üzere genişletildi. Bu destek MFC 7.0 ve üzeri ActiveX denetimi kapsayıcısı ile tamamen uyumlu olan tüm kapsayıcı içerir.  
  
 Ancak, ActiveX denetimleri olarak Windows Forms denetimleri kaydı desteklenmiyor. Ayrıca, arama `com.ms.win32.Ole32.CoCreateInstance` yöntemi Windows Forms denetimleri için desteklenmiyor. Yalnızca yönetilen etkinleştirme Windows Forms denetimleri desteklenir. Bir Windows Forms denetimi oluşturduktan sonra onu bir MFC uygulamasında olduğu gibi bir ActiveX denetimini barındırabilir.  
  
 Windows Forms denetimleri yönetilmeyen uygulamanızda kullanmak üzere API'leri barındırma yönetilmeyen CLR kullanarak CLR ana bilgisayar veya C++ birlikte çalışma özellikleri kullanmak gerekir. C++ birlikte çalışma özellikleri kullanarak önerilen bir çözümdür.  
  
## <a name="windows-forms-in-com-client-applications"></a>Windows Forms'ta COM istemci uygulamaları  
 Visual Basic 6.0 uygulaması veya bir MFC uygulaması gibi bir COM istemci uygulamasından bir Windows formu açtığınızda, form beklenmedik biçimde davranabilir. Örneğin, odak SEKME tuşuna bastığınızda, başka bir denetime bir denetimden değiştirmez. Bastığınızda ENTER tuşuna komut düğmesi odaklanmış, düğmenin ait olduğu sürece <xref:System.Windows.Forms.Control.Click> olayı oluşmaz. Ayrıca, tuş vuruşları veya fare etkinlik için beklenmeyen davranışlarla karşılaşabilirsiniz.  
  
 Yönetilmeyen uygulama Windows Forms düzgün çalışması için gerekli message döngü desteği uygulamadığından bu davranış oluşur. COM istemci uygulama tarafından sağlanan ileti döngüsü Windows Forms ileti döngüden temelde farklıdır.  
  
 Bir uygulamanın iletisi döngü bir iş parçacığının ileti kuyruğundan ileti alan bir program iç döngü bunları çevirir ve ardından bunları işlenecek uygulamaya gönderir. Windows Form için ileti döngüsü Visual Basic 6.0 uygulamaları ve MFC uygulamaları gibi daha eski uygulamalarda sağlamak ileti döngüleri aynı mimarisine sahip değil. Windows Form beklediğinden daha ileti döngüsü gönderilen pencere iletileri farklı şekilde ele alınabilir. Bu nedenle, beklenmeyen davranışları ortaya çıkabilir. Bazı tuş bileşimlerini çalışmayabilir, bazı fare etkinlik çalışmayabilir veya bazı olaylar beklendiği gibi oluşturulabilir değil.  
  
## <a name="resolving-interoperability-issues"></a>Birlikte çalışabilirlik sorunlarını çözme  
 Üzerinde formunu görüntüleyerek bu sorunları çözebilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanılarak oluşturulan ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için bir Windows Forms ileti döngüsü çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formunu görüntüleme yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte'çalışma Destek](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Her Windows formunu yeni bir iş parçacığı üzerinde görüntüleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Destek COM birlikte çalışma görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms ve Yönetilmeyen Uygulamalar](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [COM birlikte çalışabilirliği örnekleri](http://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [COM için Bütünleştirilmiş Kod Paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Bütünleştirilmiş Kodları COM ile Kaydetme](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
