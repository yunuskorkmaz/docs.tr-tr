---
description: 'Daha fazla bilgi edinin: arabirim tasarımı'
title: Arabirim Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 387f921f8bdbe6c6d398aa31dcc8a22c7da455f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641986"
---
# <a name="interface-design"></a>Arabirim Tasarımı

Çoğu API 'Ler sınıflar ve yapılar kullanılarak en iyi modellense de, arabirimlerin daha uygun veya tek seçenek olduğu durumlar vardır.

 CLR birden çok devralmayı desteklemez (yani, CLR sınıfları birden fazla taban sınıftan devralamaz), ancak türlerin bir temel sınıftan devralmaya ek olarak bir veya daha fazla arabirim uygulamasına izin verir. Bu nedenle, arabirimler genellikle birden çok devralmanın etkisini elde etmek için kullanılır. Örneğin, <xref:System.IDisposable> türlerin katılmak istedikleri diğer devralma hiyerarşisinden bağımsız olarak elden atımı desteklemesini sağlayan bir arabirimdir.

 Bir arabirimin tanımlanmasıyla ilgili diğer durum, bazı değer türleri dahil olmak üzere çeşitli türlerde desteklenebilir ortak bir arabirim oluşturmaktır. Değer türleri dışındaki türlerden devralınabilir <xref:System.ValueType> , ancak arabirimler uygulayabilir, bu nedenle ortak temel tür sağlamak için tek seçenektir.

 ✔️, bazı ortak API 'leri değer türlerini içeren bir tür kümesi tarafından desteklenmelidir.

 daha önce başka bir türden daha önce devraldığı türler üzerinde işlevselliğini desteklemeniz gerekiyorsa, bir arabirim tanımlamayı düşünün ✔️.

 ❌ İşaretleyici arabirimlerini kullanmaktan KAÇıNıN (üye olmayan arabirimler).

 Bir sınıfı belirli bir özelliğe (işaret) sahip olacak şekilde işaretlemeniz gerekiyorsa, genel olarak, bir arabirim yerine özel bir öznitelik kullanın.

 ✔️, bir arabirimin uygulanması olan en az bir tür sağlar.

 Bunu yapmak, arabirimin tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601> arabirimin bir uygulamasıdır <xref:System.Collections.Generic.IList%601> .

 ✔️, tanımladığınız her arabirimi tüketen en az bir API (bir parametre olarak arabirimi veya arabirim olarak yazılmış bir özellik) sağlar.

 Bunu yapmak, arabirim tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimini kullanır.

 ❌ Daha önce sevk edilen bir arabirime üye eklemeyin.

 Bunun yapılması, arabirimin uygulamalarını bozar. Sürüm oluşturma sorunlarından kaçınmak için yeni bir arabirim oluşturmanız gerekir.

 Bu kılavuzlar bölümünde açıklanan durumlar haricinde, genel olarak, yönetilen kod yeniden kullanılabilir kitaplıklarını tasarlarken arabirimler yerine sınıfları seçin.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
