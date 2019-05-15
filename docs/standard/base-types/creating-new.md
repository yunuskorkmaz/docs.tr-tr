---
title: . NET'te yeni dizeler oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50750b23af9e9cfca79b0f7db9d272e8e24971ab
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591407"
---
# <a name="creating-new-strings-in-net"></a>. NET'te yeni dizeler oluşturma
.NET Framework kullanarak basit atama oluşturulacak dizeleri sağlar ve ayrıca çok sayıda farklı parametreler kullanarak dize oluşturma desteklemek için bir sınıf oluşturucusu aşırı. .NET Framework içindeki çeşitli yöntemler de sağlar. <xref:System.String?displayProperty=nameWithType> yeni dize Oluştur sınıfı nesnelerini bir araya getirerek birkaç dizeleri, dize, veya nesneleri.  
  
## <a name="creating-strings-using-assignment"></a>Atama kullanarak dize oluşturma  
 Yeni bir oluşturmanın en kolay yolu <xref:System.String> nesnedir yalnızca bir dize sabit atamak için bir <xref:System.String> nesne.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Sınıf oluşturucusunu kullanarak dize oluşturma  
 Aşırı yüklemesini kullanabilirsiniz <xref:System.String> karakter dizilerden dizeleri oluşturmak için sınıf oluşturucusu. Belirli bir karakterin belirtilen sayıda çoğaltarak, yeni bir dize da oluşturabilirsiniz.  
  
## <a name="methods-that-return-strings"></a>Dizeleri döndüren yöntemler  
 Yeni dize nesneleri döndürür çeşitli kullanışlı yöntemler aşağıdaki tabloda listelenmektedir.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Biçimlendirilen dizeden Giriş bir nesne oluşturur.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|İki veya daha fazla dizeleri dizelerden oluşturur.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Dize dizisi birleştirerek yeni bir dize oluşturur.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Varolan bir dizeyi belirtilen dizine bir dize ekleyerek yeni bir dize oluşturur.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Bir dizedeki karakterleri karakter bir dizideki belirtilen bir konuma belirtilen kopyalar.|  
  
### <a name="format"></a>Biçimi  
 Kullanabileceğiniz **String.Format** biçimlendirilmiş dizeler oluşturmak ve bağlamak için yöntemi, birden çok nesneyi temsil eden dizeleri. Bu yöntem, otomatik olarak geçirilen herhangi bir nesne bir dizeye dönüştürür. Örneğin, uygulamanızın görüntülemelidir bir **Int32** değeri ve bir **DateTime** değeri kullanıcıya bir dize kullanarak bu değerleri göstermek için kolayca oluşturabilirsiniz **biçimi**yöntemi. Bu yöntemle kullanılan kuralları biçimlendirme hakkında daha fazla bilgi için üzerinde bölümüne bakın. [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 Aşağıdaki örnekte **biçimi** yöntemini kullanan bir tam sayı değişkeni bir dize.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli iş parçacığıyla ilişkilendirilmiş kültürü tarafından belirtilen şekilde geçerli tarih ve saati görüntüler.  
  
### <a name="concat"></a>concat  
 **String.Concat** yöntemi, kolayca yeni bir dize nesnesi iki veya daha fazla varolan nesnelerden oluşturmak için kullanılabilir. Dizeleri birleştirmek için bir dilden bağımsız yol sunar. Bu yöntem, türetilen herhangi bir sınıf kabul eden **System.Object**. Aşağıdaki örnek, iki var olan dize nesneleri ve ayırıcı karakteri bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Birleştirme  
 **String.Join** yöntemi, bir dizi dizeleri ve bir ayırıcı dizesinde yeni bir dize oluşturur. Bu yöntem, belki de bir virgülle ayrılmış bir listede yapmadan birlikte, birden çok dizeyi birleştirme istiyorsanız yararlı olur.  
  
 Aşağıdaki örnek, bir dize dizisi bağlamak için bir alanı kullanır.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Ekleme  
 **String.Insert** yöntemi, bir dizeyi başka bir dizede belirtilen konuma içine ekleyerek yeni bir dize oluşturur. Bu yöntem, sıfır tabanlı dizini kullanır. Aşağıdaki örnek bir dize beşinci dizin konumu ekler `MyString` ve bu değeri ile yeni bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** yöntemi, bir dizenin bölümlerini bir karakter dizisine kopyalar. Dize ve karakter kopyalanması sayısını hem başlangıç dizini belirtebilirsiniz. Bu yöntem, kaynak dizin, bir karakter dizisini, hedef dizin ve kopyalamak için karakter sayısını alır. Tüm dizinler sıfır tabanlıdır.  
  
 Aşağıdaki örnekte **CopyTo** nesnesi "bir dizeden Hello" sözcüğünü karakterleri karakter dizisi ilk dizin konumuna kopyalamak için yöntemi.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
