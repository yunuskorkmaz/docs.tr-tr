---
title: .NET ' te yeni dizeler oluşturma
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
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103825"
---
# <a name="creating-new-strings-in-net"></a>.NET ' te yeni dizeler oluşturma
.NET Framework, dizelerin basit atama kullanılarak oluşturulmasına izin verir ve ayrıca bir dizi farklı parametre kullanarak dize oluşturmayı desteklemek için bir sınıf oluşturucusunu aşırı yükler. .NET Framework Ayrıca birkaç dizeyi, dize dizilerini veya nesneleri birleştirerek yeni dize nesneleri oluşturan <xref:System.String?displayProperty=nameWithType> sınıfında çeşitli yöntemler sağlar.  
  
## <a name="creating-strings-using-assignment"></a>Atama kullanarak dizeler oluşturma  
 Yeni bir <xref:System.String> nesnesi oluşturmanın en kolay yolu, bir <xref:System.String> nesnesine bir dize sabit değeri atamanız yeterlidir.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Sınıf Oluşturucusu kullanarak dizeler oluşturma  
 Karakter dizelerinden dizeler oluşturmak için <xref:System.String> sınıf oluşturucusunun aşırı yüklerini kullanabilirsiniz. Belirli bir karakteri belirtilen sayıda çoğaltarak yeni bir dize de oluşturabilirsiniz.  
  
## <a name="methods-that-return-strings"></a>Dizeleri döndüren yöntemler  
 Aşağıdaki tabloda yeni dize nesneleri döndüren çeşitli yararlı yöntemler listelenmiştir.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Bir giriş nesneleri kümesinden biçimli bir dize oluşturur.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|İki veya daha fazla dizeden dizeler oluşturur.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Dizelerin dizisini birleştirerek yeni bir dize oluşturur.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Varolan bir dizenin belirtilen dizinine bir dize ekleyerek yeni bir dize oluşturur.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Bir dizedeki belirtilen karakterleri, bir karakter dizisinde belirtilen konuma kopyalar.|  
  
### <a name="format"></a>Biçimi  
 Biçimlendirilen dizeler oluşturmak ve birden çok nesneyi temsil eden dizeleri birleştirmek için **String. Format** yöntemini kullanabilirsiniz. Bu yöntem, geçirilen nesneleri otomatik olarak bir dizeye dönüştürür. Örneğin, uygulamanızın kullanıcıya bir **Int32** değeri ve bir **Tarih saat** değeri görüntülemesi gerekiyorsa, **Biçim** yöntemini kullanarak bu değerleri temsil eden bir dizeyi kolayca oluşturabilirsiniz. Bu yöntemle kullanılan biçimlendirme kuralları hakkında daha fazla bilgi için, [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)bölümüne bakın.  
  
 Aşağıdaki örnek, bir tamsayı değişkeni kullanan bir dize oluşturmak için **Format** yöntemini kullanır.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Bu örnekte, geçerli tarih ve saati geçerli iş parçacığıyla ilişkili kültür tarafından belirtilen şekilde görüntüler<xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
### <a name="concat"></a>Concat  
 **String. Concat** yöntemi, iki veya daha fazla var olan nesneden kolayca yeni bir dize nesnesi oluşturmak için kullanılabilir. Dizeleri birleştirmek için dile bağımsız bir yol sağlar. Bu yöntem, **System. Object**sınıfından türetilen tüm sınıfları kabul eder. Aşağıdaki örnek, iki var olan dize nesnesinden ve ayırma karakterinden oluşan bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Birleştirme  
 **String. JOIN** yöntemi bir dize dizisinden ve bir ayırıcı dizeden yeni bir dize oluşturur. Bu yöntem, birden fazla dizeyi birlikte birleştirmek istiyorsanız yararlı olur ve bir listeyi virgülle ayırarak bir liste yapar.  
  
 Aşağıdaki örnek bir dize dizisini bağlamak için bir boşluk kullanır.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Ekleme  
 **String. Insert** yöntemi, başka bir dizedeki belirtilen konuma bir dize ekleyerek yeni bir dize oluşturur. Bu yöntem sıfır tabanlı bir dizin kullanır. Aşağıdaki örnek, `MyString` beşinci dizin konumuna bir dize ekler ve bu değere sahip yeni bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String. CopyTo** yöntemi bir dizenin bölümlerini bir karakter dizisine kopyalar. Hem dizenin başlangıç dizinini hem de kopyalanacak karakter sayısını belirtebilirsiniz. Bu yöntem, kaynak dizinini, bir karakter dizisini, hedef dizini ve kopyalanacak karakter sayısını alır. Tüm dizinler sıfır tabanlıdır.  
  
 Aşağıdaki örnek, "Hello" sözcüğünün karakterlerini dize nesnesinden bir karakter dizisinin ilk dizin konumuna kopyalamak için **CopyTo** yöntemini kullanır.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
