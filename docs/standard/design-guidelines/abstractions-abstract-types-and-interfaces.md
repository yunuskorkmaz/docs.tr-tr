---
title: Soyutlamalar (Soyut Türler ve Arabirimler)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: fd5b8fe10d0dcca5da3a2093f7be37f6d88b382a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280620"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Soyutlamalar (Soyut Türler ve Arabirimler)
Soyutlama, sözleşmeyi tanımlayan, ancak sözleşmenin tam bir uygulamasını sağlamayan bir türdür. Soyutlamalar genellikle soyut sınıflar veya arabirimler olarak uygulanır ve sözleşmeyi uygulayan türlerin gereken semantiğini açıklayan, iyi tanımlanmış bir başvuru belgeleri kümesiyle gelir. .NET Framework en önemli soyutlamalar şunlardır <xref:System.IO.Stream> , <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Object> .

 Bir soyutlamayı destekleyen somut bir tür uygulayarak ve soyutlamayı kullanan (üzerinde çalışan) çerçeve API 'Leriyle bu somut türü kullanarak çerçeveleri genişletebilirsiniz.

 Zamanı test etmek mümkün olan anlamlı ve yararlı bir soyutlama tasarlamak çok zordur. Ana zorluk, daha fazla ve daha az olmayan, doğru üye kümesini alıyor. Soyutlama çok fazla üyeye sahipse, uygulanması zor veya imkansız olur. Taahhüt edilen işlevsellik için çok az üye varsa, bu çok sayıda ilginç senaryo için kullanılamaz hale gelir.

 Çerçevede çok fazla soyut olan soyutlamalar ayrıca Framework kullanılabilirliğini olumsuz etkiler. Somut uygulamaların ve soyutlama üzerinde çalışan API 'lerin daha büyük resmine ne kadar uygun olduğunu anlamak zorunda kalmadan bir soyutlamayı anlamak oldukça zordur. Ayrıca, soyutlamalar ve üyelerinin adları soyut hale gelir, bu da genellikle kullanımının daha geniş bir bağlamını anlamak zorunda kalmadan şifreli ve unapproachable.

 Ancak soyutlamalar, diğer genişletilebilirlik mekanizmalarının sıklıkla eşleşemesinden çok güçlü bir genişletilebilirlik sağlar. Eklentiler, denetim (IOC), işlem hatları vb. gibi birçok mimari deseninden oluşur. Çerçeveler için test edilebilirlik için de oldukça önemlidir. İyi soyutlamalar, birim testi amacıyla ağır bağımlılıkların yerine koymasını mümkün kılar. Özet olarak, modern nesne yönelimli çerçevelerin zenginleştirmesinden sonra soyutlamalar sorumludur.

 ❌Soyutlamaları kullanan çeşitli somut uygulamalar ve API 'Ler geliştirilirken test olmadıkları müddetçe soyutlamalar sağlamayan.

 bir soyutlama tasarlarken bir soyut sınıf ve arabirim arasında dikkatli bir şekilde seçim YAPıN. ✔️

 ✔️ Soyut uygulamaların somut uygulamaları için başvuru testleri sağlamayı düşünün. Bu tür testler, kullanıcıların, sözleşmesinin sözleşmeyi doğru şekilde uygulayıp uygulamadığını test etmelerini sağlar.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
