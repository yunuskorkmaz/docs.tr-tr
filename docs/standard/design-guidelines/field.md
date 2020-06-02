---
title: Alan Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289752"
---
# <a name="field-design"></a>Alan Tasarımı
Kapsülleme prensibi, nesne odaklı tasarımda en önemli olmaların biridir. Bu ilke, bir nesne içinde depolanan verilerin yalnızca o nesnenin erişimine açık olması gerektiğini belirtir.

 Prensibi yorumlamak için kullanışlı bir yol, türün (ad veya tür değişiklikleri) alanlara yapılan değişikliklerin, türün üyeleri için dışında bir kod olmadan yapılabilmesi için bir türün tasarlanmalıdır. Bu yorum hemen tüm alanların özel olması gerektiğini gösterir.

 Bu katı kısıtlamadan yalnızca sabit ve statik salt okunurdur alanları hariç tutduk, çünkü bu tür alanlar, neredeyse tanım için hiçbir şekilde değişiklik gerektirmez.

 ❌Ortak veya korumalı örnek alanlarını sağlamaın.

 Genel veya korumalı hale getirmek yerine alanlara erişim için özellikler sağlamalısınız.

 ✔️ hiçbir şekilde değişmeyecek sabitler için sabit alanlar kullanın.

 Derleyici const alanlarının değerlerini doğrudan çağıran koda dönüştürür. Bu nedenle, sabit değerler hiçbir şekilde uyumluluk riski olmadan değiştirilemez.

 ✔️ `readonly` önceden tanımlanmış nesne örnekleri için ortak statik alanları kullanın.

 Türün önceden tanımlanmış örnekleri varsa, bunları türün kendisine ait public salt okunurdur statik alanlar olarak bildirin.

 ❌Alanlara kesilebilir türlerin örneklerini atamayın `readonly` .

 Kesilebilir tür, örneklendirildikten sonra değiştirilebilen örneklere sahip bir türdür. Örneğin, diziler, en çok koleksiyonlar ve akışlar değişebilir türlerdir, ancak, <xref:System.Int32?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> ve <xref:System.String?displayProperty=nameWithType> sabittir. Bir başvuru türü alanındaki salt okunurdur değiştirici, alanda depolanan örneğin değiştirilmesini önler, ancak örneği değiştiren Üyeler çağırarak alanın örnek verilerinin değiştirilmesini engellemez.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
