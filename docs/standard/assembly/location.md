---
title: Derleme konumu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973182"
---
# <a name="assembly-location"></a>Derleme konumu
Bir derlemenin konumu, ortak dil çalışma zamanının başvurulması sırasında bulup belirleyemeyeceğini belirler ve derlemenin diğer Derlemelerle paylaşılıp paylaşılamayacağını da tespit edebilir. Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:  
  
- Uygulamanın dizini veya alt dizinleri.  
  
     Bu, bir derlemeyi dağıtmaya yönelik en yaygın konumdur. Bir uygulamanın kök dizininin alt dizinleri dil veya kültür temelinde olabilir. Bir derlemenin kültür özniteliğinde bilgileri varsa, bu kültür adına sahip uygulama dizini altındaki bir alt dizinde olmalıdır.  
  
- Genel derleme önbelleği.  
  
     Bu, ortak dil çalışma zamanının yüklendiği her yerde yüklenen makine genelindeki bir kod önbelleğidir. Çoğu durumda, birden çok uygulamayla bir derlemeyi paylaşmayı düşünüyorsanız, onu genel derleme önbelleğine dağıtmanız gerekir.  
  
- Bir HTTP sunucusunda.  
  
     HTTP sunucusunda dağıtılan bir derlemenin tanımlayıcı adı olması gerekir; uygulamanın yapılandırma dosyasının kod temeli bölümünde derleme üzerine gelin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler oluştur](create.md)
- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Bütünleştirilmiş kod içeren program](program.md)
