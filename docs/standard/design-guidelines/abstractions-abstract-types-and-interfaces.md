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
ms.openlocfilehash: 014144764609c8a7faa87f3d080900824f9189eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709588"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Soyutlamalar (Soyut Türler ve Arabirimler)
Soyutlama, sözleşmeyi tanımlayan, ancak sözleşmenin tam bir uygulamasını sağlamayan bir türdür. Soyutlamalar genellikle soyut sınıflar veya arabirimler olarak uygulanır ve sözleşmeyi uygulayan türlerin gereken semantiğini açıklayan, iyi tanımlanmış bir başvuru belgeleri kümesiyle gelir. .NET Framework en önemli soyutlamalar <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>ve <xref:System.Object>içerir.  
  
 Bir soyutlamayı destekleyen somut bir tür uygulayarak ve soyutlamayı kullanan (üzerinde çalışan) çerçeve API 'Leriyle bu somut türü kullanarak çerçeveleri genişletebilirsiniz.  
  
 Zamanı test etmek mümkün olan anlamlı ve yararlı bir soyutlama tasarlamak çok zordur. Ana zorluk, daha fazla ve daha az olmayan, doğru üye kümesini alıyor. Soyutlama çok fazla üyeye sahipse, uygulanması zor veya imkansız olur. Taahhüt edilen işlevsellik için çok az üye varsa, bu çok sayıda ilginç senaryo için kullanılamaz hale gelir.  
  
 Çerçevede çok fazla soyut olan soyutlamalar ayrıca Framework kullanılabilirliğini olumsuz etkiler. Somut uygulamaların ve soyutlama üzerinde çalışan API 'lerin daha büyük resmine ne kadar uygun olduğunu anlamak zorunda kalmadan bir soyutlamayı anlamak oldukça zordur. Ayrıca, soyutlamalar ve üyelerinin adları soyut hale gelir, bu da genellikle kullanımının daha geniş bir bağlamını anlamak zorunda kalmadan şifreli ve unapproachable.  
  
 Ancak soyutlamalar, diğer genişletilebilirlik mekanizmalarının sıklıkla eşleşemesinden çok güçlü bir genişletilebilirlik sağlar. Eklentiler, denetim (IOC), işlem hatları vb. gibi birçok mimari deseninden oluşur. Çerçeveler için test edilebilirlik için de oldukça önemlidir. İyi soyutlamalar, birim testi amacıyla ağır bağımlılıkların yerine koymasını mümkün kılar. Özet olarak, modern nesne yönelimli çerçevelerin zenginleştirmesinden sonra soyutlamalar sorumludur.  
  
 **X DO NOT** birkaç somut uygulamaları ve soyutlama kullanan API'ler geliştirerek sınanır sürece soyutlamalar sağlar.  
  
 **✓ DO** bir Özet tasarlarken, bir Özet sınıf arasında bir arabirim dikkatle seçin.  
  
 **✓ CONSIDER** başvuru testleri soyutlamalar somut uygulamaları için sağlama. Bu tür testler, kullanıcıların, sözleşmesinin sözleşmeyi doğru şekilde uygulayıp uygulamadığını test etmelerini sağlar.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
