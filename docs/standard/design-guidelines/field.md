---
description: 'Daha fazla bilgi edinin: alan tasarımı'
title: Alan Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 88df60c3050035221dc65429bbd543c71d5d69b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642051"
---
# <a name="field-design"></a>Alan Tasarımı

Kapsülleme prensibi, nesne odaklı tasarımda en önemli olmaların biridir. Bu ilke, bir nesne içinde depolanan verilerin yalnızca o nesnenin erişimine açık olması gerektiğini belirtir.

 Prensibi yorumlamak için kullanışlı bir yol, türün (ad veya tür değişiklikleri) alanlara yapılan değişikliklerin, türün üyeleri için dışında bir kod olmadan yapılabilmesi için bir türün tasarlanmalıdır. Bu yorum hemen tüm alanların özel olması gerektiğini gösterir.

 Bu katı kısıtlamadan yalnızca sabit ve statik salt okunurdur alanları hariç tutduk, çünkü bu tür alanlar, neredeyse tanım için hiçbir şekilde değişiklik gerektirmez.

 ❌ Ortak veya korumalı örnek alanlarını sağlamaın.

 Genel veya korumalı hale getirmek yerine alanlara erişim için özellikler sağlamalısınız.

 ✔️ hiçbir şekilde değişmeyecek sabitler için sabit alanlar kullanın.

 Derleyici const alanlarının değerlerini doğrudan çağıran koda dönüştürür. Bu nedenle, sabit değerler hiçbir şekilde uyumluluk riski olmadan değiştirilemez.

 ✔️ `readonly` önceden tanımlanmış nesne örnekleri için ortak statik alanları kullanın.

 Türün önceden tanımlanmış örnekleri varsa, bunları türün kendisine ait public salt okunurdur statik alanlar olarak bildirin.

 ❌ Alanlara kesilebilir türlerin örneklerini atamayın `readonly` .

 Kesilebilir tür, örneklendirildikten sonra değiştirilebilen örneklere sahip bir türdür. Örneğin, diziler, en çok koleksiyonlar ve akışlar değişebilir türlerdir, ancak, <xref:System.Int32?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> ve <xref:System.String?displayProperty=nameWithType> sabittir. Bir başvuru türü alanındaki salt okunurdur değiştirici, alanda depolanan örneğin değiştirilmesini önler, ancak örneği değiştiren Üyeler çağırarak alanın örnek verilerinin değiştirilmesini engellemez.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
