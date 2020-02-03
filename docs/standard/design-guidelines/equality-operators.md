---
title: Eşitlik İşleçleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741697"
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölümde eşitlik işleçlerini aşırı yükleme ve `operator==` ve eşitlik işleçleri olarak `operator!=` açıklanır.

 ❌ eşitlik işleçlerinden birini aşırı yüklemeyin.

 ✔️ <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiğe ve benzer performans özelliklerine sahip olduğundan emin olun.

 Bu genellikle eşitlik işleçleri aşırı yüklendiğinde `Object.Equals` geçersiz kılınmasının gerektiği anlamına gelir.

 ❌ eşitlik işleçlerinden özel durumlar oluşturmaktan kaçının.

 Örneğin, `NullReferenceException`yapmak yerine bağımsız değişkenlerden biri null ise false döndürün.

## <a name="equality-operators-on-value-types"></a>Değer türlerinde eşitlik Işleçleri
 eşitlik anlamlı ise, değer türlerinde eşitlik işleçlerini aşırı yükleme ✔️.

 Çoğu programlama dilinde, değer türleri için `operator==` varsayılan bir uygulama yoktur.

## <a name="equality-operators-on-reference-types"></a>Başvuru türlerinde eşitlik Işleçleri
 ❌ kesilebilir başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.

 Birçok dilde başvuru türleri için yerleşik eşitlik işleçleri vardır. Yerleşik operatörler genellikle başvuru eşitliğini uygular ve varsayılan davranış değer eşitliğine değiştirildiğinde çok sayıda geliştirici şaşırtır.

 Bu sorun, sabit başvuru türleri için azaltıldığı için, değişiklik, başvuru eşitliği ve değer eşitlik arasındaki farkı fark ettiğini çok daha zor hale getirir.

 ❌, başvuru eşitlemeden önemli ölçüde daha yavaş olacaksa, başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
