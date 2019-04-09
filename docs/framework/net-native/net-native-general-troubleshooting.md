---
title: .NET Yerel Genel Sorun Giderme
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81ff8a347235ab1a765b4f41051dab2da786b89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150780"
---
# <a name="net-native-general-troubleshooting"></a>.NET Yerel Genel Sorun Giderme
Bu konu ile uygulamalar geliştirirken karşılaşabileceğiniz olası sorunların nasıl giderileceği açıklanmaktadır [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   **Sorun:** Yapı çıktı penceresini düzgün şekilde güncelleştirilmez.  
  
     **Çözüm:** Yapı tamamlanana kadar yapı çıkış penceresinde güncelleştirilmez. Derleme zamanlarını karşılaşabileceğiniz için birkaç dakika kadar güncelleştirmeler görmeye bir gecikme olabilir.  
  
-   **Sorun:** ARM için uygulamanızın perakende derleme süresi arttı.  
  
     **Çözüm:** ARM cihazınıza bir uygulamayı dağıttığınızda [!INCLUDE[net_native](../../../includes/net-native-md.md)] altyapı çağrılır. Bu derleme yansıma devam gibi çalışması, statik olmayan semantiğe sağlarken çok sayıda iyileştirmeleri gerçekleştirir. Ayrıca, uygulamanın kullandığı .NET Framework'ün bir bölümü, MFC'ye statik olarak en iyi performans için bağlı olan ve de yerel kod içine derlenmiş gerekir. Derleme daha uzun sürer nedeni budur.  
  
     Ancak, yine de dakikadır standart geliştirme makinesindeki çoğu uygulama standart bir derleme içinde derleme sürelerini uygulanır.  Genellikle, yalnızca standart geliştirmenin bir makinede .NET Framework için yerel görüntüler oluşturuluyor, birkaç dakika sürer.  Oluşturulan kodun geliştirmek için bile tüm iyileştirmeler ve .NET Framework dahil olmak üzere ile uygulama derleme süreleri genellikle bir veya iki dakika olduğundan.  
  
     Çok iş parçacıklı derleme ve diğer iyileştirmeler incelenerek derleme performansı iyileştirme üzerinde çalışmaya devam ediyoruz.  
  
-   **Sorun:** Uygulamanızı kullanarak derlenen bilmiyorum [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Çözüm:** Varsa [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici çağrılır, artık kez yapı fark edeceksiniz ve Görev Yöneticisi'ni çeşitli gösterir [!INCLUDE[net_native](../../../includes/net-native-md.md)] bileşenini işlemlerin ILC.exe ve nutc_driver.exe gibi.  
  
     Başarıyla projenizi derledikten sonra [!INCLUDE[net_native](../../../includes/net-native-md.md)], çıkış obj altında bulabilirsiniz\\*config*\ *arch* \\  *ProjectName*. ilc\out.  Yerel son paket içeriğinin depo altında bulunabilir\\*arch*\\*config*\AppX. Son Yerel Paket içeriğini \bin altında olan\\*arch*\\*config*uygulama dağıttıysanız \AppX.  
  
-   **Sorun:** .NET yerel olarak derlenmiş uygulamanızı, çalışma zamanı özel durumları atma (genellikle [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) veya [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar), ne zaman oluşturmadı emin olmadan derlenir. Yerel ağ.  
  
     **Çözüm:** .NET Native meta veriler ya da aksi takdirde yansıma yoluyla kullanılabilir uygulama kodu sağlamadığından özel durumlar. (Daha fazla bilgi için [.NET Native ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).) Özel durumu ortadan kaldırmak için bir girdi eklemeniz gerekir, [çalışma zamanı yönergeleri (rd.xml) dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) .NET Native araç zinciri meta veri veya uygulama kodunu kullanılabilir çalışma zamanında yapabilmeleri için. İki sorun gidericileri kullanılabilir çalışma zamanı yönergeleri dosyanıza eklemek için gerekli giriş oluşturacağını:  
  
    -   [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
    -   [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
     Daha fazla bilgi için [yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
