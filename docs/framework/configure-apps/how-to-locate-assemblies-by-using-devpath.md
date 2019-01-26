---
title: 'Nasıl yapılır: DEVPATH kullanarak derlemelerin bulun'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 0d238ceb4f96905031cb4a30f50727050381277e
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084503"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Nasıl yapılır: DEVPATH kullanarak derlemelerin bulun
Geliştiriciler, oluşturmakta olduğunuz paylaşılan bir derleme birden çok uygulama ile doğru şekilde çalıştığından emin olmak isteyebilirsiniz. Geliştirme döngüsü sırasında genel derleme önbelleğinde sürekli derleme almak yerine Geliştirici derlemesi için derleme çıktı dizinine işaret eden bir DEVPATH ortam değişkeni oluşturabilirsiniz.  
  
 Örneğin, MySharedAssembly adlı paylaşılan bir derleme oluşturuyorsanız ve çıkış dizini C:\MySharedAssembly\Debug olduğunu varsayın. DEVPATH değişkeninde C:\MySharedAssembly\Debug koyabilirsiniz. Ardından belirtmelisiniz [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) makine yapılandırma dosyasındaki öğesi. Bu öğe DEVPATH derlemeleri bulmak için kullanılacak ortak dil çalışma zamanı söyler.  
  
 Paylaşılan derleme çalışma zamanı tarafından bulunabilir olması gerekir.  Bütünleştirilmiş kod başvuruları kullanımı çözümlemek için özel bir dizin belirtmek için [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) veya [ \<yoklama > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) bölümünde anlatıldığı gibi bir yapılandırma dosyası [Bir derlemenin konumunu belirtme](../../../docs/framework/configure-apps/specify-assembly-location.md).  Ayrıca, uygulama dizininin bir alt dizinde derleme koyabilirsiniz. Daha fazla bilgi için [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Yalnızca geliştirme için hedeflenen bir Gelişmiş özelliğinin budur.  
  
 Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinlerde arama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Bu ayar varsayılan olarak false.  
  
> [!NOTE]
>  Yalnızca geliştirme sırasında bu ayarı kullanın. Çalışma zamanı, tanımlayıcı adlı derlemeler DEVPATH içinde bulunan sürümlerinde denetlemez. Yalnızca bulduğu ilk derlemeyi de kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [.NET Framework uygulamalarını yapılandırma](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
