---
title: Tanımlayıcı Adlı Derlemeler
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f283aad7c6727aff111aaaf78beb1e8da4b45898
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988368"
---
# <a name="strong-named-assemblies"></a>Tanımlayıcı Adlı Derlemeler
Derlemeyi güçlü adlandırma derleme için benzersiz bir kimlik oluşturur ve derleme çakışmalarını önleyebilir.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Tanımlayıcı adlı bütünleştirilmiş kod ne olur?  
 Tanımlayıcı adlı bütünleştirilmiş kod, derleme ile dağıtılan ortak anahtara karşılık gelen özel anahtar kullanılarak oluşturulur ve derlemenin kendisi olur. Bütünleştirilmiş kod, derlemeyi oluşturan tüm dosyaların adlarını ve karmalarını içeren derleme bildirimini içerir. Aynı tanımlayıcı ada sahip derlemeler özdeş olmalıdır.  
  
 Visual Studio 'Yu veya bir komut satırı aracını kullanarak derlemeleri kesin olarak ad olarak belirleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi tanımlayıcı ad](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) veya [sn. exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)ile imzalayın.  
  
 Tanımlayıcı adlı bir derleme oluşturulduğunda, derleme basit metin adını, sürüm numarasını, isteğe bağlı kültür bilgilerini, dijital imzayı ve imza için kullanılan özel anahtara karşılık gelen ortak anahtarı içerir.  
  
> [!WARNING]
> Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.  
  
## <a name="why-strong-name-your-assemblies"></a>Derlemelerinize neden güçlü ad adı veriyor?  
 Tanımlayıcı adlı bir derlemeye başvuru yaptığınızda, sürüm oluşturma ve adlandırma koruması gibi belirli avantajları de bekleyebilir. Tanımlayıcı adlı derlemeler, bazı senaryoları etkinleştirmek için gerekli olan genel derleme önbelleğine yüklenebilir.  
  
 Tanımlayıcı adlı derlemeler aşağıdaki senaryolarda faydalıdır:  
  
- Derlemelerinize tanımlayıcı adlı derlemeler tarafından başvurulmak üzere veya tanımlayıcı adlı diğer derlemelerden derlemelerinize erişim vermek `friend` isteyebilirsiniz.  
  
- Uygulamanın aynı derlemenin farklı sürümlerine erişmesi gerekir. Bu, çakışma olmadan aynı uygulama etki alanında yan yana yüklemek üzere bir derlemenin farklı sürümlerinin olması gerektiği anlamına gelir. Örneğin, aynı basit ada sahip derlemelerde bir API 'nin farklı uzantıları varsa, güçlü adlandırma derlemenin her sürümü için benzersiz bir kimlik sağlar.  
  
- Derlemenizi kullanarak uygulamaların performansını olumsuz şekilde etkilememesini istemezsiniz, bu nedenle derlemenin etki alanı nötr olmasını isteyebilirsiniz. Bu, genel derleme önbelleğine bir etki alanı nötr derleme yüklenmesi gerektiğinden, güçlü adlandırma gerektirir.  
  
- Yayımcı ilkesi uygulayarak uygulamanızın bakımını yapmak istediğinizde, derlemenin genel derleme önbelleğinde yüklü olması gerektiği anlamına gelir.  
  
 Açık kaynaklı bir geliştiricisiyseniz ve tanımlayıcı adlı bir derlemenin kimlik avantajlarından yararlanmak istiyorsanız, bir derlemeyle ilişkili özel anahtarı kaynak denetim sisteminize iade etmeyi düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
