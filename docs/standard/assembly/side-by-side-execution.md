---
title: Derlemeler ve yan yana yürütme
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138650"
---
# <a name="assemblies-and-side-by-side-execution"></a>Derlemeler ve yan yana yürütme

Yan yana yürütme, aynı bilgisayarda bir uygulama veya bileşenin birden çok sürümünü saklama ve yürütme olanağıdır. Bu da ortak dil çalışma zamanı sürümünün birden çok sürümünün ve çalışma zamanının bir sürümünü kullanan uygulama ve bileşenlerin birden çok sürümünün bir bilgisayar üzerinde aynı anda bulunabileceği anlamına gelir. Yan yana yürütme olanağı, bir uygulamanın bir bileşenin hangi sürümüne bağlanacağını ve bir uygulamanın hangi çalışma zamanını kullanacağı konusunda daha fazla denetim sağlar.  
  
Aynı derlemenin farklı sürümlerinin yan yana depolanması ve yürütülmesi için sunulan destek, tanımlayıcı adlandırmanın temel bir parçasıdır ve çalışma zamanının altyapısında yerleşik olarak bulunmaktadır. Tanımlayıcı ada sahip olan derlemenin sürüm numarası kimliğinin bir parçası olduğundan, çalışma zamanı aynı derlemenin birden çok sürümünü genel derleme önbelleğinde tutabilir ve çalışma zamanında bu derlemeleri yükleyebilir.  
  
Çalışma zamanı size yan yana uygulamalar oluşturma olanağı sağlasa da yan yana yürütme otomatik değildir. Yan yana yürütme için uygulama oluşturma hakkında daha fazla bilgi [için, yan yana yürütme için bileşenler oluşturmak için Yönergeler'e](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
