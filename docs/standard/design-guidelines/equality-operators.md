---
title: Eşitlik İşleçleri
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 85a9e81d28995229e6b47d7fe4d0b541265999f8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821352"
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölüm, eşitlik işleçlerini aşırı yüklemeyi ve `operator==` `operator!=` eşitlik işleçlerini gösterir.

 ❌ Farklı bir eşitlik işleçlerinden birini aşırı yüklemeyin.

 ✔️, <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçlerinin tam olarak aynı semantiğe ve benzer performans özelliklerine sahip olduğundan emin olun.

 Bu genellikle `Object.Equals` eşitlik işleçleri aşırı yüklendiğinde geçersiz kılınması gereken anlamına gelir.

 ❌ Eşitlik işleçlerinden özel durumlar oluşturmaktan kaçının.

 Örneğin, bağımsız değişkenlerden biri oluşturmak yerine null ise false döndürün `NullReferenceException` .

## <a name="equality-operators-on-value-types"></a>Değer türlerinde eşitlik Işleçleri
 eşitlik anlamlı ise, değer türlerinde eşitlik işleçlerini aşırı yükleme ✔️.

 Çoğu programlama dilinde, değer türleri için varsayılan bir uygulama yoktur `operator==` .

## <a name="equality-operators-on-reference-types"></a>Başvuru türlerinde eşitlik Işleçleri
 ❌ Değişebilir başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.

 Birçok dilde başvuru türleri için yerleşik eşitlik işleçleri vardır. Yerleşik operatörler genellikle başvuru eşitliğini uygular ve varsayılan davranış değer eşitliğine değiştirildiğinde çok sayıda geliştirici şaşırtır.

 Bu sorun, sabit başvuru türleri için azaltıldığı için, değişiklik, başvuru eşitliği ve değer eşitlik arasındaki farkı fark ettiğini çok daha zor hale getirir.

 ❌ Uygulama, başvuru eşitlemeden önemli ölçüde daha yavaş olacaksa, başvuru türlerinde eşitlik işleçlerini aşırı yüklemeden KAÇıNıN.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)
