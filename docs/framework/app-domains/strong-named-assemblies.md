---
title: Tanımlayıcı Adlı Derlemeler
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f87fb330fbea1344cc8532519d358fe8580a9fd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592698"
---
# <a name="strong-named-assemblies"></a>Tanımlayıcı Adlı Derlemeler
Tanımlayıcı adlandırma bir derleme, derleme için benzersiz kimlik oluşturur ve birleştirme çakışmalarını engelleyebilir.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Bir katı adlı derleme yapan nedir?  
 Güçlü adlı bir derleme, derleme ve derlemenin kendisini dağıtılmış ortak anahtarına karşılık gelen özel anahtar kullanılarak oluşturulur. Derleme adları ve derlemeyi oluşturan tüm dosyaların karma değerlerini içeren derleme bildirimini içerir. Aynı tanımlayıcı ada sahip derlemelerin aynı olmalıdır.  
  
 Tanımlayıcı ad derlemeleri, Visual Studio veya bir komut satırı aracını kullanarak yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Bir katı adlı derleme oluşturulduğunda derleme, sürüm numarası, isteğe bağlı bir kültür bilgilerini, bir dijital imza ve imzalama için kullanılan özel anahtarına karşılık gelen ortak anahtarı basit metin adı içerir.  
  
> [!WARNING]
>  Güvenlik için tanımlayıcı adlar güvenmeyin. Benzersiz bir kimliğe sağlarlar.  
  
## <a name="why-strong-name-your-assemblies"></a>Tanımlayıcı ad neden bütünleştirilmiş kodlarınızı?  
 Tanımlayıcı adlı bütünleştirilmiş kod başvurduğunuzda, sürüm oluşturma ve adlandırma koruma gibi belirli avantajlardan bekleyebilirsiniz. Tanımlayıcı adlandırılmış derlemeler genel bütünleştirilmiş kod, bazı senaryoları etkinleştirmek için gereken önbelleğinde yüklenebilir.  
  
 Tanımlayıcı adlandırılmış derlemeler, aşağıdaki senaryolarda kullanışlıdır:  
  
- Tanımlayıcı adlı derlemeler tarafından başvurulabilmesi bütünleştirilmiş kodlarınızı etkinleştirmek istediğiniz veya vermek istediğiniz `friend` diğer tanımlayıcı adlı derlemeler bütünleştirilmiş kodlarınızı erişim.  
  
- Bir uygulamanın, aynı derlemenin farklı sürümlerine erişim gerekir. Bu, farklı sürümlerini yan yana çakışma olmadan aynı uygulama etki alanında yüklemek için bir derleme ihtiyacınız olduğu anlamına gelir. Farklı bir API Uzantıları basit aynı ada sahip derlemelerde varsa, örneğin, güçlü adlandırma benzersiz bir kimliğe her derlemenin sürüm için sağlar.  
  
- Derleme etki alanı nötr olarak istediğiniz şekilde derlemenizi kullanarak uygulama performansını olumsuz istemezsiniz. Bir etki alanından bağımsız derleme genel derleme önbelleğine yüklenmelidir çünkü bu güçlü adlandırma gerektirir.  
  
- Uygulamanız için yayımcı ilkesi uygulayarak bakım merkezileştirmek istiyorsanız, derleme başka bir deyişle, genel derleme önbelleğinde yüklü olmalıdır.  
  
 Bir açık kaynak geliştiricisi olan ve bir tanımlayıcı adlı bütünleştirilmiş kod kimliği avantajlarını istiyorsanız bir derlemeye kaynak denetim sisteminiz ile ilişkili özel anahtarı denetlemeyi düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Nasıl yapılır: Derlemeyi tanımlayıcı bir adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
