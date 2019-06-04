---
title: Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 137aeaab4e63adbb81c0f3d90718def10f906e6a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489240"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri

.NET Framework 4 ile başlayarak, ortak dil çalışma zamanı tür bilgilerini katıştırma COM türleri için doğrudan birlikte çalışma derlemeleri COM türleri için tür bilgisi almak Yönetilen derlemeler yerine Yönetilen derlemeler içine destekler. Gömülü tür bilgileri yalnızca türler ve gerçekten yönetilen bir derleme tarafından kullanılan üyeler içerdiğinden, iki Yönetilen derlemeler çok farklı görünümleri aynı COM tür olabilir. Yönetilen her derlemenin farklı bir sahip <xref:System.Type> COM türü onun görünümünü temsil eden nesne. Ortak dil çalışma zamanı tür denklik arabirimleri, yapılar, sabit listeleri ve temsilciler için bu farklı görünümleri arasında destekler.

Tür eşdeğerliği birinden diğerine yönetilen bütünleştirilmiş kod uygun olarak atanabilir geçirilen bir COM nesnesi türü alma derlemedeki yönetilen anlamına gelir.

> [!NOTE]
> Birlikte çalışma derlemeleriyle uygulamaları dağıtmak gerekli olmadığından tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri, uygulamaların dağıtımını ve COM bileşenlerini kullanmak eklentileri basitleştirin. Geliştiricilerin paylaşılan COM bileşenlerinin, yine de .NET Framework'ün önceki sürümleri tarafından kullanılan bileşenleri istediğinde birincil birlikte çalışma derlemeleri (PIA) oluşturmanız gerekir.

## <a name="type-equivalence"></a>Tür denkliği

 COM tür denklik arabirimleri, yapılar, sabit listeleri ve temsilciler için desteklenir. COM türleri, aşağıdakilerin tümü doğru olduğunda denk olarak uygun:

- , Hem arabirimleri veya hem yapıları veya hem sabit listeleri veya her iki temsilci türleridir.

- Sonraki bölümde açıklandığı gibi türleri aynı kimliğe sahip.

- Her iki türü de açıklandığı gibi tür denklik için uygun olan [işaretleme COM türleri tür eşdeğerliğine için](#marking-com-types-for-type-equivalence) bölümü.

### <a name="type-identity"></a>Tür kimliği

İki tür, kapsamları ve kimlikler, diğer bir deyişle, eşleştiğinde her varsa aynı kimliğe sahip belirlenir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği ve iki öznitelik sahip eşleşen <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ve <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özellikleri. Karşılaştırma için <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> büyük küçük harfe duyarlıdır.

Bir tür yoksa <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği veya varsa bir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> belirtmiyor kapsamı ve tanımlayıcı, türü özniteliği hala olarak kabul edilir denklik için şu şekilde:

- Arabirimlerin, değerini <xref:System.Runtime.InteropServices.GuidAttribute> yerine kullanılan <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği (ad alanı dahil diğer bir deyişle, tür adını) yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> özelliği.

- Yapılar, sabit listeleri ve Temsilciler <xref:System.Runtime.InteropServices.GuidAttribute> içeren derlemenin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özelliği.

### <a name="marking-com-types-for-type-equivalence"></a>COM türleri tür eşdeğerliğine için işaretleme

 Bir tür için iki yolla türü eşdeğerlik uygun olarak işaretleyebilirsiniz:

- Uygulama <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> öznitelik türü için.

- Türünün bir COM içeri aktarma türü olmasını sağlayın. Bu arabirim bir COM içeri aktarma türü ise <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliği. Derleme içinde tanımlanmış olduğu bir arabirim, yapı, sabit listesi veya temsilci bir COM içeri aktarma türü ise <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> özniteliği.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.IsEquivalentTo%2A>
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
