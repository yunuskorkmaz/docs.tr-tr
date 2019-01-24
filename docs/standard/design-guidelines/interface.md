---
title: Arabirim tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660157"
---
# <a name="interface-design"></a>Arabirim tasarımı
Çoğu API'ler, en iyi sınıfları ve yapıları kullanarak modellenir olsa da, arabirimler daha uygun olan veya tek seçenektir durumlar vardır.  
  
 CLR'nin birden çok devralmayı desteklemez (yani, CLR sınıflarını birden fazla temel sınıfından devralamaz), ancak bir taban sınıftan devralmayı ek olarak, bir veya daha fazla arabirimi uygulayan türleri sağlar. Bu nedenle, arabirimler, genellikle birden çok devralma etkiyi elde etmek için kullanılır. Örneğin, <xref:System.IDisposable> disposability, istedikleri katılmak diğer tüm Devralma Hiyerarşisi bağımsız desteklemek için türleri izin veren bir arabirimdir.  
  
 Hangi tanımlama arabirimin uygun olan diğer bazı değer türleri dahil olmak üzere çeşitli türleri tarafından desteklenen ortak bir arabirim oluştururken bir durumdur. Değer türleri devralamaz türlerinden dışında <xref:System.ValueType>, ancak arabirimleri uygulayabilir, bunu bir arabirimi kullanarak ortak bir taban türü sağlamak için tek seçenek.  
  
 **✓ DO** değer türleri içeren bir dizi türleri tarafından desteklenen bazı ortak API gerekiyorsa bir arabirim tanımlayın.  
  
 **✓ CONSIDER** önceden başka bazı türünden devralan türleri işlevselliği desteklemek gereksinim duyarsanız bir arabirim tanımlama.  
  
 **X AVOID** işaret arabirimleri (hiçbir üye arabirimleriyle) kullanarak.  
  
 Genel olarak, belirli bir karakteristik (işaretçi) sahip bir sınıfı işaretlemek gerekiyorsa, bir arabirim yerine özel bir öznitelik kullanın.  
  
 **✓ DO** bir arabirim uygulaması en az bir türü sağlar.  
  
 Arabirim tasarımı doğrulamak için bu yardımcı yapılıyor. Örneğin, <xref:System.Collections.Generic.List%601> uygulamasıdır <xref:System.Collections.Generic.IList%601> arabirimi.  
  
 **✓ DO** tanımladığınız her bir arabirime tüketir en az bir API sağlar (bir parametre veya bir özellik arabirimi alma yöntemi yazılan arabirimi olarak).  
  
 Arabirim tasarımı doğrulamak için bu yardımcı yapılıyor. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> tüketir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimi.  
  
 **X DO NOT** önceden sevk edilmiş bir arabirim üye ekleyin.  
  
 Bunun yapılması uygulamaları arabiriminin bölün. Sürüm oluşturma sorunları önlemek için yeni bir arabirim oluşturmanız gerekir.  
  
 Bu yönergelere uymanız açıklanan durumlar hariç, genel olarak, arabirimler yerine sınıfları yönetilen kod yeniden kullanılabilir kitaplıklar tasarlama seçtiğiniz gerekir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
