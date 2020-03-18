---
title: .NET'te Yeni Dizeleri Oluşturma
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103825"
---
# <a name="creating-new-strings-in-net"></a>.NET'te Yeni Dizeleri Oluşturma
.NET Framework dizeleri basit atama kullanılarak oluşturulacak sağlar ve aynı zamanda farklı parametreler bir dizi kullanarak dize oluşturma desteklemek için bir sınıf oluşturucu aşırı yükler. .NET Framework ayrıca, çeşitli <xref:System.String?displayProperty=nameWithType> dizeleri, dize dizileri veya nesneleri birleştirerek yeni dize nesneleri oluşturmak sınıfta çeşitli yöntemler sağlar.  
  
## <a name="creating-strings-using-assignment"></a>Atamayı Kullanarak Dizeleri Oluşturma  
 Yeni <xref:System.String> bir nesne oluşturmanın en kolay yolu, bir <xref:System.String> nesneye bir dize harfi atamaktır.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Sınıf Oluşturucu sularını kullanarak dizeler oluşturma  
 Karakter dizilerinden dizeleri <xref:System.String> oluşturmak için sınıf oluşturucu aşırı yüklerini kullanabilirsiniz. Ayrıca, belirli bir karakteri belirli bir sayıda çoğaltarak yeni bir dize oluşturabilirsiniz.  
  
## <a name="methods-that-return-strings"></a>Dizeleri Döndüren Yöntemler  
 Aşağıdaki tabloda yeni dize nesneleri döndüren birkaç yararlı yöntem listelenilmiştir.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Giriş nesneleri kümesinden biçimlendirilmiş bir dize oluşturur.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|İki veya daha fazla dizeden dizeleri oluşturur.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Bir dizi dizeyi birleştirerek yeni bir dize oluşturur.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Varolan bir dizenin belirtilen dizinine bir dize ekleyerek yeni bir dize oluşturur.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Bir dizedeki belirtilen karakterleri bir dizi karakterde belirtilen konuma kopyalar.|  
  
### <a name="format"></a>Biçimlendir  
 Biçimlendirilmiş dizeleri oluşturmak ve birden çok nesneyi temsil eden dizeleri birleştirmek için **String.Format** yöntemini kullanabilirsiniz. Bu yöntem, geçirilen herhangi bir nesneyi otomatik olarak bir dize dönüştürür. Örneğin, uygulamanızın kullanıcıya bir **Int32** değeri ve **DateTime** değeri görüntülemesi gerekiyorsa, **Biçim** yöntemini kullanarak bu değerleri temsil edecek bir dize kolayca oluşturabilirsiniz. Bu yöntemle kullanılan biçimlendirme kuralları hakkında bilgi için [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)bölümüne bakın.  
  
 Aşağıdaki örnekte, tamsayı değişkeni kullanan bir dize oluşturmak için **Biçim** yöntemi ni kullanır.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Bu örnekte,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> geçerli tarih ve saati geçerli iş parçacığıyla ilişkili kültür tarafından belirtilen şekilde görüntüler.  
  
### <a name="concat"></a>Concat  
 **String.Concat** yöntemi, varolan iki veya daha fazla nesneden kolayca yeni bir dize nesnesi oluşturmak için kullanılabilir. Dizeleri biraraya getirmek için dilden bağımsız bir yol sağlar. Bu yöntem **System.Object**türetilen herhangi bir sınıf kabul eder. Aşağıdaki örnek, varolan iki dize nesnesinden bir dize ve ayıran bir karakter oluşturur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Birleştir  
 **String.Join** yöntemi, bir dizi dize ve ayırıcı dizeden yeni bir dize oluşturur. Bu yöntem, birden çok dizeleri bir araya getirmek istiyorsanız, belki virgülle ayrılmış bir liste yapmak yararlıdır.  
  
 Aşağıdaki örnek, bir dize dizisini bağlamak için bir boşluk kullanır.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Ekle  
 **String.Insert** yöntemi, başka bir dizede belirli bir konuma bir dize ekleyerek yeni bir dize oluşturur. Bu yöntem, sıfır tabanlı dizin kullanır. Aşağıdaki örnek, beşinci dizin konumuna bir `MyString` dize ekler ve bu değere sahip yeni bir dize oluşturur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** yöntemi, bir dizebölümlerini bir karakter dizisine kopyalar. Hem dizenin başlangıç dizinini hem de kopyalanacak karakter sayısını belirtebilirsiniz. Bu yöntem kaynak dizini, bir karakter dizisini, hedef dizini ve kopyalanması gereken karakter sayısını alır. Tüm dizinler sıfır tabanlıdır.  
  
 Aşağıdaki örnek, "Merhaba" sözcüğünün karakterlerini bir dize nesnesinden bir dizi karakterin ilk dizin konumuna kopyalamak için **CopyTo** yöntemini kullanır.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
