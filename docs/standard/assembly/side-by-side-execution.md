---
title: Derlemeler ve yan yana yürütme
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6f5d4b6bf94300872f85c118bd149d12cea65d0
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973070"
---
# <a name="assemblies-and-side-by-side-execution"></a>Derlemeler ve yan yana yürütme
Yan yana yürütme, aynı bilgisayarda bir uygulama veya bileşenin birden çok sürümünü saklama ve yürütme olanağıdır. Bu da ortak dil çalışma zamanı sürümünün birden çok sürümünün ve çalışma zamanının bir sürümünü kullanan uygulama ve bileşenlerin birden çok sürümünün bir bilgisayar üzerinde aynı anda bulunabileceği anlamına gelir. Yan yana yürütme olanağı, bir uygulamanın bir bileşenin hangi sürümüne bağlanacağını ve bir uygulamanın hangi çalışma zamanını kullanacağı konusunda daha fazla denetim sağlar.  
  
 Aynı derlemenin farklı sürümlerinin yan yana depolanması ve yürütülmesi için sunulan destek, tanımlayıcı adlandırmanın temel bir parçasıdır ve çalışma zamanının altyapısında yerleşik olarak bulunmaktadır. Tanımlayıcı ada sahip olan derlemenin sürüm numarası kimliğinin bir parçası olduğundan, çalışma zamanı aynı derlemenin birden çok sürümünü genel derleme önbelleğinde tutabilir ve çalışma zamanında bu derlemeleri yükleyebilir.  
  
 Çalışma zamanı size yan yana uygulamalar oluşturma olanağı sağlasa da yan yana yürütme otomatik değildir. Yan yana yürütmeye yönelik uygulamalar oluşturma hakkında daha fazla bilgi için bkz. [yan yana yürütme için bileşen oluşturmaya yönelik yönergeler](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
