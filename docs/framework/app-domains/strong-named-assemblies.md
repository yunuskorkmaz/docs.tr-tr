---
title: "Tanımlayıcı Adlı Derlemeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1d9fb79fa6c58ada7c342bd1d56281c3fbab900
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strong-named-assemblies"></a>Tanımlayıcı Adlı Derlemeler
Güçlü adlandırma bütünleştirilmiş, derleme için benzersiz bir kimliği oluşturur ve derleme çakışmaları engelleyebilirsiniz.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derleme ne yapar?  
 Güçlü bir adlandırılmış derleme, derlemeyi ve derleme ile dağıtılmış ortak anahtara karşılık gelen özel anahtarı kullanılarak oluşturulur. Derleme adları ve derlemeyi oluşturan tüm dosyaların karmaları içeren derleme bildirimi içerir. Güçlü ile aynı ada sahip bir derleme aynı olmalıdır.  
  
 Tanımlayıcı ad derlemeleri Visual Studio veya komut satırı aracını kullanarak yapabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Tanımlayıcı adlı bir derleme oluşturulduğunda, derleme, sürüm numarası, isteğe bağlı kültür bilgilerini, dijital imza ve imzalama için kullanılan özel anahtarına karşılık gelen ortak anahtarı düz metin adını içerir.  
  
> [!WARNING]
>  Güvenlik tanımlayıcı adlar kullanmayın. Yalnızca benzersiz bir kimlik sağlarlar.  
  
## <a name="why-strong-name-your-assemblies"></a>Tanımlayıcı adlı neden derlemeleriniz?  
 Tanımlayıcı adlı bir bütünleştirilmiş koda başvurduğunuzda, sürüm oluşturma ve koruma adlandırma gibi bazı avantajları bekleyebilirsiniz. Tanımlayıcı adlı derlemeler genel bütünleştirilmiş kod, bazı senaryoları etkinleştirmek için gereken önbelleğinde yüklenebilir.  
  
 Tanımlayıcı adlı derlemeler aşağıdaki senaryolarda kullanışlıdır:  
  
-   Tanımlayıcı adlı derlemeler tarafından başvurulan derlemeleriniz etkinleştirmek istediğiniz ya da vermek istediğiniz `friend` diğer tanımlayıcı adlı derlemeler derlemeleriniz erişim.  
  
-   Bir uygulama aynı derlemenin farklı sürümleri erişimi olmalıdır. Başka bir deyişle, çakışma yaşamadan aynı uygulama etki alanında yan yana yüklemek için bir derlemenin farklı sürümleri gerekir. Farklı uzantılar bir API'nin basit ile aynı ada sahip derlemelerde varsa, örneğin, güçlü adlandırma benzersiz bir kimlik derleme her sürümü için sağlar.  
  
-   Etki alanı dilden bağımsız olarak derleme istediğiniz şekilde derlemenizi kullanarak uygulamaları performansını olumsuz etmek istiyor musunuz. Bir etki alanı Tarafsız derleme genel derleme önbelleğinde yüklenmesi gerektiğinden bu güçlü adlandırma gerektirir.  
  
-   Yayımcı ilkesi uygulayarak uygulamanız için bakım merkezileştirmek istediğinizde, genel derleme önbelleğinde derleme başka bir deyişle, yüklenmelidir.  
  
 Bir açık kaynak Geliştirici misiniz ve kesin adlandırılmış bir derleme kimlik yararları istediğiniz kaynak denetim sisteminiz derlemeye ilişkili özel anahtarı denetimini düşünün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
