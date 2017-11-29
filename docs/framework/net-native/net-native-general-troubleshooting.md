---
title: .NET Yerel Genel Sorun Giderme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 151a36eed22323c32fed93a88d8270bdbfd99061
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="net-native-general-troubleshooting"></a>.NET Yerel Genel Sorun Giderme
Bu konu ile uygulamaları geliştirirken karşılaşabileceğiniz olası sorunları gidermek nasıl açıklar [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   **Sorun:** yapı çıktı penceresi düzgün şekilde güncelleştirilmez.  
  
     **Çözüm:** yapı tamamlanana kadar yapı çıktı penceresi güncelleştirilmez. Yapı zamanları karşılaşabileceğiniz için birkaç dakika kadar güncelleştirmeleri görmesini bir gecikme olabilir.  
  
-   **Sorun:** ARM artırmıştır için uygulamanızın perakende derleme zamanı.  
  
     **Çözüm:** ARM Cihazınızı bir uygulama dağıttığınızda [!INCLUDE[net_native](../../../includes/net-native-md.md)] altyapı çağrılır. Bu derleme yansıma devam gibi çalışması, statik olmayan semantiği sağlarken en iyi duruma getirme, çok sayıda gerçekleştirir. Ayrıca, uygulamanın kullandığı .NET Framework kısmı statik olarak en iyi performans için bağlı ve de yerel koda derlenmiş gerekir. Derleme daha uzun sürer nedeni budur.  
  
     Ancak, derleme sürelerini hala dakikadır standart geliştirme makinedeki çoğu uygulamalarında standart derleme ağdadır.  Genellikle, yalnızca .NET Framework standart geliştirme makinede yerel görüntüler oluşturmak birkaç dakika sürer.  Oluşturulan kod geliştirmek için bile tüm en iyi duruma getirme ile .NET Framework dahil olmak üzere, uygulama yapı kez genellikle bir veya iki dakika olur.  
  
     Çok iş parçacıklı derleme ve diğer en iyi duruma getirme incelenerek derleme performansı iyileştirme çalışmaya devam ediliyor.  
  
-   **Sorun:** uygulamanızı kullanılarak derlendi tanımadığınız [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Çözüm:** varsa [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici çağrıldığında, artık kez derleme görürsünüz ve Görev Yöneticisi'ni çeşitli gösterir [!INCLUDE[net_native](../../../includes/net-native-md.md)] ILC.exe ve nutc_driver.exe gibi bileşen işlemler.  
  
     Projenizi ile başarıyla yapı sonra [!INCLUDE[net_native](../../../includes/net-native-md.md)], çıktı obj altında bulabilirsiniz\\*config*\ *arch* \\  *ProjectName*. ilc\out.  Son Yerel Paket içeriğini depo altında bulunabilir\\*arch*\\*config*\AppX. Son Yerel Paket içeriğini \bin altında olan\\*arch*\\*config*uygulamayı dağıttıysanız \AppX.  
  
-   **Sorun:** .NET yerel koda derlenmiş uygulama çalışma zamanı özel durumları atma (genellikle [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) veya [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar), onu belirtmiyor .NET yerel derlendiğinde atar.  
  
     **Çözüm:** .NET yerel meta verileri veya aksi halde yansıma yoluyla kullanılabilir uygulama kodu sağlamadığından özel durumlar. (Daha fazla bilgi için bkz: [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).) Bir giriş eklemek zorunda özel ortadan kaldırmak için [çalışma zamanı yönergeleri (rd.xml) dosya](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) .NET yerel araç zinciri meta veri veya uygulama kodunu kullanılabilir çalışma zamanında böylece yapabilirsiniz. İki sorun gidericileri kullanılabilir çalışma zamanı yönergeleri dosyasına eklemek için gerekli giriş üretir:  
  
    -   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
    -   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
     Daha fazla bilgi için bkz: [yansıma ve .NET yerel](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows mağazası uygulamanızı .NET Yerel'e taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
