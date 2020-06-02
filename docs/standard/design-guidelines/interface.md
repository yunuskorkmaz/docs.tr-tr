---
title: Arabirim Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: f589d47d5b945179430275598996b2fb77e92848
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289037"
---
# <a name="interface-design"></a>Arabirim Tasarımı
Çoğu API 'Ler sınıflar ve yapılar kullanılarak en iyi modellense de, arabirimlerin daha uygun veya tek seçenek olduğu durumlar vardır.

 CLR birden çok devralmayı desteklemez (yani, CLR sınıfları birden fazla taban sınıftan devralamaz), ancak türlerin bir temel sınıftan devralmaya ek olarak bir veya daha fazla arabirim uygulamasına izin verir. Bu nedenle, arabirimler genellikle birden çok devralmanın etkisini elde etmek için kullanılır. Örneğin, <xref:System.IDisposable> türlerin katılmak istedikleri diğer devralma hiyerarşisinden bağımsız olarak elden atımı desteklemesini sağlayan bir arabirimdir.

 Bir arabirimin tanımlanmasıyla ilgili diğer durum, bazı değer türleri dahil olmak üzere çeşitli türlerde desteklenebilir ortak bir arabirim oluşturmaktır. Değer türleri dışındaki türlerden devralınabilir <xref:System.ValueType> , ancak arabirimler uygulayabilir, bu nedenle ortak temel tür sağlamak için tek seçenektir.

 ✔️, bazı ortak API 'leri değer türlerini içeren bir tür kümesi tarafından desteklenmelidir.

 daha önce başka bir türden daha önce devraldığı türler üzerinde işlevselliğini desteklemeniz gerekiyorsa, bir arabirim tanımlamayı düşünün ✔️.

 ❌İşaretleyici arabirimlerini kullanmaktan KAÇıNıN (üye olmayan arabirimler).

 Bir sınıfı belirli bir özelliğe (işaret) sahip olacak şekilde işaretlemeniz gerekiyorsa, genel olarak, bir arabirim yerine özel bir öznitelik kullanın.

 ✔️, bir arabirimin uygulanması olan en az bir tür sağlar.

 Bunu yapmak, arabirimin tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601> arabirimin bir uygulamasıdır <xref:System.Collections.Generic.IList%601> .

 ✔️, tanımladığınız her arabirimi tüketen en az bir API (bir parametre olarak arabirimi veya arabirim olarak yazılmış bir özellik) sağlar.

 Bunu yapmak, arabirim tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimini kullanır.

 ❌Daha önce sevk edilen bir arabirime üye eklemeyin.

 Bunun yapılması, arabirimin uygulamalarını bozar. Sürüm oluşturma sorunlarından kaçınmak için yeni bir arabirim oluşturmanız gerekir.

 Bu kılavuzlar bölümünde açıklanan durumlar haricinde, genel olarak, yönetilen kod yeniden kullanılabilir kitaplıklarını tasarlarken arabirimler yerine sınıfları seçin.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
