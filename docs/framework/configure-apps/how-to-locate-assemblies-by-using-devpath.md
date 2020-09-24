---
title: 'Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma'
description: Bir XML bilgisayar yapılandırma dosyası ve DEVPATH ortam değişkeni kullanarak, paylaşılan bir derlemenin .NET 'teki birçok uygulamayla doğru şekilde çalışıp çalışmadığını test edin.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 8ae807e46b11d2adb06d6af0c86e1c7297caa0c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161990"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma

Geliştiriciler, oluşturmakta oldukları paylaşılan bir derlemenin birden çok uygulamayla doğru şekilde çalıştığından emin olmak isteyebilir. Geliştirici, geliştirme çevrimi sırasında derlemeyi genel bütünleştirilmiş kod önbelleğine sürekli koymak yerine, derleme için derleme çıkış dizinini işaret eden bir DEVPATH ortam değişkeni oluşturabilir.  
  
 Örneğin, MySharedAssembly adlı bir paylaşılan derleme oluşturduğunuzu ve çıkış dizininin C:\mysharedassembly\debugolduğunu varsayalım. C:\MySharedAssembly\Debug öğesini DEVPATH değişkenine yerleştirebilirsiniz. Ardından, [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) öğesini makine yapılandırma dosyasında belirtmeniz gerekir. Bu öğe, ortak dil çalışma zamanına derlemeleri bulmak için DEVPATH kullanmasını söyler.  
  
 Paylaşılan derleme çalışma zamanı tarafından bulunabilir olmalıdır.  Derleme başvurularını çözümlemek için özel bir dizin belirtmek üzere [derleme konumunu belirtme](specify-assembly-location.md)bölümünde [ \<probing> açıklandığı](./file-schema/runtime/probing-element.md) gibi bir yapılandırma dosyasındaki [ \<codeBase> öğesini](./file-schema/runtime/codebase-element.md) veya öğesini kullanın.  Derlemeyi uygulama dizininin bir alt dizininde de yerleştirebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Bu, yalnızca geliştirme için tasarlanan gelişmiş bir özelliktir.  
  
 Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Bu ayar varsayılan olarak false değerini alır.  
  
> [!NOTE]
> Bu ayarı yalnızca geliştirme zamanında kullanın. Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez. Yalnızca bulduğu ilk derlemeyi kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma](index.md)
