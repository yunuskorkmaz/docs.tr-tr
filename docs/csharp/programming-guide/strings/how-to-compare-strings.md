---
title: "Nasıl yapılır: dizeleri (C# programlama Kılavuzu) karşılaştırma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4837fa57c962cba841ffcc83c5bd4475a4faff0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-strings-c-programming-guide"></a>Nasıl yapılır: dizeleri (C# programlama Kılavuzu) karşılaştırma

Dizeleri karşılaştırmak, bir dize belirten bir sonuç oluşturan veya diğer'den büyük veya iki dizeyi eşit olmalıdır. Tarafından sonucu belirlenen kurallar olup gerçekleştirdiğiniz bağlı olarak farklı *sıralı karşılaştırma* veya *kültüre duyarlı karşılaştırma*. Belirli bir görev için karşılaştırma doğru türünü kullanmak önemlidir.

 Temel sıralı karşılaştırmaları karşılaştırmak ya da dil kuralları dikkate almaksızın iki dize değerlerini sıralamak sahip olduğunuzda kullanın. Temel sıralı karşılaştırma (`System.StringComparison.Ordinal`), küçük harf duyarlıdır iki dizeyi karakter karakter eşleşmelidir anlamına gelir: "ve" eşit değil "Ve" veya "Ve". Bir sık kullanılan çeşitlemedir `System.StringComparison.OrdinalIgnoreCase`, hangi eşleşir "ve", "Ve" ve "Ve". `StringComparison.OrdinalIgnoreCase`genellikle dosya adları, yol adları, ağ yollarını ve kullanıcının bilgisayarına bölgesel ayarına göre değeri değişmeyen herhangi bir dize karşılaştırmak için kullanılır. Daha fazla bilgi için bkz. <xref:System.StringComparison?displayProperty=nameWithType>.

 Kültüre duyarlı karşılaştırmaları genellikle karşılaştırın ve son kullanıcılar tarafından Giriş dizeleri karakterler ve sıralama kuralları bu dizeler, kullanıcının bilgisayarındaki yerel ayara bağlı olarak farklı olabileceğinden dolayı sıralamak için kullanılır. Aynı karakterler içeren bile dizeleri geçerli iş parçacığı kültürünü bağlı olarak farklı sıralama.

> [!NOTE]
> Dizeleri karşılaştırmak olduğunda, gerçekleştirmek istediğiniz karşılaştırma türünü açıkça belirtmek yöntemlerini kullanmanız gerekir. Bu, çok daha sürdürülebilir ve okunabilir kodunuzu kolaylaştırır. Mümkün olduğunda, aşırı yöntemlerinden birini kullanın <xref:System.String?displayProperty=nameWithType> ve <xref:System.Array?displayProperty=nameWithType> sınıfları süren bir <xref:System.StringComparison> numaralandırma parametresinin, böylece gerçekleştirmek için karşılaştırma türünü belirtebilirsiniz. Kullanmaktan kaçınmak en iyisidir `==` ve `!=` dizeleri karşılaştırdığınızda işleçler. Ayrıca, kullanmaktan kaçının <xref:System.String.CompareTo%2A?displayProperty=nameWithType> aşırı hiçbiri aldığından yöntemleri örnek bir <xref:System.StringComparison>.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, doğru kullanıcının bilgisayarı bölgesel ayarına göre değerleri değişmez dizeleri karşılaştırmak gösterilmektedir. Ayrıca, aynı zamanda gösterir *dize interning* C# özelliğidir. İki veya daha çok özdeş dizesi değişkenlerinin bir program bildirir, derleyici bunların tümü aynı konumda depolar. Çağırarak <xref:System.Object.ReferenceEquals%2A> yöntemi, iki dizeyi aslında aynı nesneye bellekte başvurmadığından görebilirsiniz. Kullanım <xref:System.String.Copy%2A?displayProperty=nameWithType> interning, örnekte gösterildiği gibi önlemek için yöntem.

[!code-csharp[csProgGuideStrings#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, tercih edilen yol kullanarak dizeleri karşılaştırmak gösterilmiştir <xref:System.String?displayProperty=nameWithType> ele yöntemleri bir <xref:System.StringComparison> numaralandırması. Unutmayın <xref:System.String.CompareTo%2A?displayProperty=nameWithType> örnek yöntemleri kullanılmaz burada aşırı hiçbiri aldığından bir <xref:System.StringComparison>.

[!code-csharp[csProgGuideStrings#31](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#31)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl sıralanacağını gösterir ve bir dizi bir kültüre duyarlı şekilde statik kullanarak dizeleri arama <xref:System.Array> ele yöntemleri bir <xref:System.StringComparer?displayProperty=nameWithType> parametresi.

[!code-csharp[csProgGuideStrings#32](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#32)]

Koleksiyon sınıfları gibi <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ele oluşturucular sahip bir <xref:System.StringComparer?displayProperty=nameWithType> öğeleri veya anahtarları türünü olduğunda parametre `string`. Genel olarak, mümkün olduğunda bu oluşturucular kullanın ve gerekir ya da belirtin `Ordinal` veya `OrdinalIgnoreCase`.

## <a name="see-also"></a>Ayrıca bkz.
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)  
 [Dizeleri karşılaştırma](../../../standard/base-types/comparing.md)  
 [Uygulamaları Genelleştirme ve yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications)