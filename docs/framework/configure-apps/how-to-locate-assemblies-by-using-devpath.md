---
title: 'Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912994"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma
Geliştiriciler, oluşturmakta oldukları paylaşılan bir derlemenin birden çok uygulamayla doğru şekilde çalıştığından emin olmak isteyebilir. Geliştirici, geliştirme çevrimi sırasında derlemeyi genel bütünleştirilmiş kod önbelleğine sürekli koymak yerine, derleme için derleme çıkış dizinini işaret eden bir DEVPATH ortam değişkeni oluşturabilir.  
  
 Örneğin, MySharedAssembly adlı bir paylaşılan derleme oluşturduğunuzu ve çıkış dizininin C:\mysharedassembly\debugolduğunu varsayalım. C:\MySharedAssembly\Debug öğesini DEVPATH değişkenine yerleştirebilirsiniz. Daha sonra, makine yapılandırma dosyasında [ \<DevelopmentMode >](./file-schema/runtime/developmentmode-element.md) öğesini belirtmeniz gerekir. Bu öğe, ortak dil çalışma zamanına derlemeleri bulmak için DEVPATH kullanmasını söyler.  
  
 Paylaşılan derleme çalışma zamanı tarafından bulunabilir olmalıdır.  Derleme başvurularını çözümlemek için özel bir dizin belirtmek üzere [derleme konumunu belirtme](specify-assembly-location.md)bölümünde açıklandığı gibi bir yapılandırma dosyasında [ \<codebase > element](./file-schema/runtime/codebase-element.md) veya [ \<yoklama > öğesini](./file-schema/runtime/probing-element.md) kullanın.  Derlemeyi uygulama dizininin bir alt dizininde de yerleştirebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).  
  
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

- [Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](index.md)
