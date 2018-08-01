---
title: Eşitlik İşleçleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1e5784de277d59c7bc945cbe7b605653eec7bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571023"
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölümde tekrar yüklemesi eşitlik işleçleri açıklanır ve başvurduğu `operator==` ve `operator!=` eşitlik işleçleri olarak.  
  
 **X DO NOT** eşitlik işleçleri ve diğer aşırı yükleme.  
  
 **✓ DO** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.  
  
 Bu genellikle anlamına `Object.Equals` eşitlik işleçleri aşırı zaman geçersiz kılınacak gerekiyor.  
  
 **X AVOID** eşitlik işleçleri özel durumları atma.  
  
 Örneğin, bağımsız değişkenlerden biri atma yerine null ise false döndürür `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Değer türleri üzerinde eşitlik işleçleri  
 **✓ DO** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Çoğu programlama dillerinde hiçbir varsayılan uygulaması olduğundan `operator==` değer türleri için.  
  
## <a name="equality-operators-on-reference-types"></a>Başvuru türleri üzerinde eşitlik işleçleri  
 **X AVOID** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Birçok dilin başvuru türleri için yerleşik eşitlik işleçleri vardır. Yerleşik genellikle başvuru eşitliği işleçler ve varsayılan davranışı için değer eşitliği değiştirildiğinde, geliştiricilerin çoğu Şaşkın.  
  
 Girişi çok referans eşitlik ve değer eşitliği arasındaki fark zorlaştıran çünkü bu sorunu değişmez başvuru türlerinde azalır.  
  
 **X AVOID** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
