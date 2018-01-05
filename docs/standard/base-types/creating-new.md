---
title: ".NET ile yeni dizeler oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ba91b42bc9815b1b12fdc761882741b11790060
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-new-strings-in-net"></a>.NET ile yeni dizeler oluşturma
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Basit atama kullanılarak oluşturulması dizeleri sağlar ve aynı zamanda çok sayıda farklı parametreler kullanarak dize oluşturma desteklemek için bir sınıf oluşturucu overloads. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ayrıca çeşitli yöntemlerin sağlar <xref:System.String?displayProperty=nameWithType> yeni bir dize oluşturma sınıf nesneleri birkaç dizeleri, dizeleri, dizilerin birleştirerek veya nesneleri.  
  
## <a name="creating-strings-using-assignment"></a>Atama kullanarak dizeler oluşturma  
 Yeni bir oluşturmanın en kolay yolu <xref:System.String> nesnesidir yalnızca bir dize sabit değeri için atamak için bir <xref:System.String> nesnesi.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Bir sınıf oluşturucu kullanılarak dizeler oluşturma  
 Aşırı kullanabilirsiniz <xref:System.String> karakter dizileri dizesi oluşturmak için sınıfı oluşturucusu. Belirli bir karakterin belirtilen sayıda çoğaltarak, yeni bir dize de oluşturabilirsiniz.  
  
## <a name="methods-that-return-strings"></a>Dizeleri döndüren yöntemler  
 Aşağıdaki tabloda yeni dize nesneler döndürmeye birkaç yararlı yöntemleri listelenmiştir.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Giriş nesneler kümesinden biçimlendirilmiş bir dize oluşturur.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|İki veya daha fazla dizelerden oluşturur.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Dize dizisi birleştiren yeni bir dize oluşturur.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Varolan bir dizeyi belirtilen dizine bir dize ekleyerek yeni bir dize oluşturur.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Bir dizedeki karakterleri karakter dizideki belirlenen bir konuma belirtilen kopyalar.|  
  
### <a name="format"></a>Biçimi  
 Kullanabileceğiniz **String.Format** biçimlendirilmiş dizeler oluşturmak ve bağlamak için yöntem dizeleri birden çok nesneyi temsil eden. Bu yöntem, otomatik olarak geçirilen nesnelere bir dizeye dönüştürür. Örneğin, uygulamanızın görüntülemeniz gerekir, bir **Int32** değeri ve **DateTime** değeri kullanıcıya kullanarak bu değerleri temsil eden bir dize kolayca oluşturabileceğiniz **biçimi**yöntemi. Bu yöntemle kullanılan kuralları biçimlendirme hakkında daha fazla bilgi için bölümüne bakarak [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 Aşağıdaki örnek kullanır **biçimi** yöntemi kullanan bir tamsayı değişken bir dize oluşturma.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli iş parçacığı ile ilişkili kültür tarafından belirtilen şekilde geçerli tarih ve saati görüntüler.  
  
### <a name="concat"></a>concat  
 **String.Concat** yöntemi, kolayca yeni bir dize nesnesi iki veya daha fazla var olan nesneleri oluşturmak için kullanılabilir. Dizeyi birleştirmek için dil bağımsız bir yol sağlar. Bu yöntem, türetilen herhangi bir sınıf kabul eder **System.Object**. Aşağıdaki örnekte, iki mevcut string nesneleri ve ayıran karakter bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Birleştirme  
 **String.Join** yöntemi, bir dizi dizeler ve ayırıcı dize yeni bir dize oluşturur. Bu yöntem belki de virgülle ayrılmış bir listede yapmadan birlikte, birden çok dizeyi birleştirme istiyorsanız kullanışlıdır.  
  
 Aşağıdaki örnekte bir alan bir dize dizisi bağlamak için kullanır.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Ekleme  
 **String.Insert** yöntemi, başka bir dize olarak belirtilen bir konuma bir dize ekleyerek yeni bir dize oluşturur. Bu yöntem, sıfır tabanlı bir dizin kullanır. Aşağıdaki örnek bir dize beşinci dizin konumunu ekler `MyString` ve bu değeri ile yeni bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** yöntemi dize bölümlerini karakterden oluşan bir diziye kopyalar. Dize kopyalanacak karakter sayısını ve her iki başlangıç dizini belirtebilirsiniz. Bu yöntem, kaynak dizin, bir karakter dizisi, hedef dizin ve kopyalamak için karakter sayısını alır. Tüm dizinler sıfır tabanlı.  
  
 Aşağıdaki örnek kullanır **CopyTo** "bir dizeden Hello" ifadesini nesne word'ün karakterleri karakter ilk dizin konumuna kopyalamak için yöntem.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
 [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
