---
title: Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a014058feb2ccb5187081fc63fb9c6eb6ac53d41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607564"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
Hizmet verilen bileşenlerin (yönetilen kod COM + bileşenleri) genel derleme önbelleğinde koymanız gerekir. Bazı senaryolarda, COM + Hizmetleri ve ortak dil çalışma zamanı genel derleme önbelleğinde olmayan hizmet verilen bileşenleri işleyebilir; Diğer senaryolarda yapamazlar. Aşağıdaki senaryolar bu göstermektedir:  
  
- Bir COM + sunucu uygulamasında hizmet verilen bileşenleri için servis verilen bileşenleri içeren aynı dizinde Dllhost.exe çalışmadığından bileşenlerini içeren derleme genel derleme önbelleğinde olması gerekir.  
  
- Bir COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + Hizmetleri geçerli dizinde arama yaparak bileşenleri içeren derlemenin başvurusunu çözebilirsiniz. Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.  
  
- Bir ASP.NET uygulamasında hizmet verilen bileşenleri için durum farklıdır. Uygulama temel bin dizininde servis verilen bileşenleri içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanıyorsanız, ASP.NET çalışma zamanı gölge yeteneklerini kullanır çünkü derleme indirme önbelleğe gölge kopyalar olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
