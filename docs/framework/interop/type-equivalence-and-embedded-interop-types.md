---
title: "Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b29ed1c3659b1705640888ded5fe21432dc6ada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri
İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], doğrudan birlikte çalışma derlemeleri COM türleri için tür bilgisi almak Yönetilen derlemeler gerektirmek yerine Yönetilen derlemeler içine COM türleri için tür bilgilerini katıştırma ortak dil çalışma zamanı destekler. Gömülü tür bilgileri yalnızca türleri ve gerçekte yönetilen derlemesi tarafından kullanılan üyeler içerdiği için iki Yönetilen derlemeler çok farklı görünümleri aynı COM türde olabilir. Her yönetilen derleme farklı bir sahip <xref:System.Type> COM türünün kendi görünümünü temsil eden nesne. Ortak dil çalışma zamanı tür denkliği arabirimleri, yapıları, numaralandırmalar ve temsilciler için bu farklı görünümleri arasında destekler.  
  
 Tür denkliği yönetilen alıcı derlemesindeki türü bir yönetilen derleme başka bir uygun atanabilecek geçirilen bir COM nesnesi anlamına gelir.  
  
> [!NOTE]
>  Uygulamaları ile birlikte çalışma derlemeleri dağıtmak gerekli olmadığından, uygulamaların dağıtımını ve COM bileşenlerini kullanmak eklentiler tür eşdeğerliği ve katıştırılmış birlikte çalışma türlerini basitleştirin. Paylaşılan COM bileşenlerini geliştiricileri yine .NET Framework'ün önceki sürümleri tarafından kullanılacak bileşenleri istiyorsanız birincil birlikte çalışma derlemeleri (PIA) oluşturmanız gerekir.  
  
## <a name="type-equivalence"></a>Tür denkliği  
 COM türlerinin eşdeğer arabirimleri, yapıları, numaralandırmalar ve temsilciler için desteklenir. Aşağıdakilerin tümü doğruysa, COM türlerini eşdeğer olarak nitelemek:  
  
-   , Hem arabirimleri veya hem yapıları veya hem numaralandırmalar veya her iki temsilciler türleridir.  
  
-   Türleri, sonraki bölümde açıklandığı gibi aynı kimliğe sahip.  
  
-   Bölümünde açıklandığı gibi her iki tür denkliği için uygun olan [COM türlerinde işaretleme tür denkliği](#type_equiv) bölümü.  
  
### <a name="type-identity"></a>Tür kimliği  
 İki tür kendi kapsamları ve kimlikler, diğer bir deyişle, eşleştiğinde her varsa aynı kimliğe sahip belirlenir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliğine ve iki özelliklere sahip eşleşen <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ve <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özellikleri. Karşılaştırma için <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> büyük küçük harfe duyarlıdır.  
  
 Bir tür yoksa <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği veya varsa bir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> belirtmiyor kapsamı ve tanımlayıcı olarak türü özniteliği hala sayılabileceğini için eşdeğer gibi:  
  
-   Arabirimler, değeri için <xref:System.Runtime.InteropServices.GuidAttribute> yerine kullanılan <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği (ad alanı dahil diğer bir deyişle, tür adını) yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> özelliği.  
  
-   Yapılar, numaralandırmalar ve Temsilciler <xref:System.Runtime.InteropServices.GuidAttribute> içeren derlemenin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> özelliği ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özelliği.  
  
<a name="type_equiv"></a>   
### <a name="marking-com-types-for-type-equivalence"></a>COM türleri tür denkliği için işaretleme  
 Bir tür için iki yolla tür denkliği uygun olarak işaretleyebilirsiniz:  
  
-   Uygulama <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> öznitelik türü.  
  
-   Türünün bir COM alma türü olmasını sağlayın. Bu arabirim COM alma türü ise <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliği. İçinde tanımlanmış derleme bir arabirim, yapısı, numaralandırma veya temsilci COM alma türü ise <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type.IsEquivalentTo%2A>  
 [Yönetilen kodda COM türlerini kullanma](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [Tür kitaplığını derleme olarak içeri aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
