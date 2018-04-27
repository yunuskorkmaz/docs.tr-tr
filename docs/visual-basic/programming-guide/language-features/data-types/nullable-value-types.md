---
title: Boş Değer Atanabilen Değer Türleri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16df20be89a88aa68e06692594c208cee1ab2dea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="nullable-value-types-visual-basic"></a>Boş Değer Atanabilen Değer Türleri (Visual Basic)
Bazen tanımlı bir değer bazı durumlarda sahip olmayan bir değer türü ile çalışır. Örneğin, bir veritabanı alanına anlamlı atanmış bir değere sahip ve atanmış bir değere sahip değil ayırt etmek zorunda kalabilirsiniz. Değer türleri normal değerlerine veya null değeri olması için genişletilebilir. Böyle bir uzantı olarak adlandırılan bir *boş değer atanabilir tür*.  
  
 Boş değer atanabilir her tür genel oluşturulan <xref:System.Nullable%601> yapısı. İş ilgili etkinlikleri izleyen bir veritabanı göz önünde bulundurun. Aşağıdaki örnek null atanabilir yapıları `Boolean` yazın ve bu tür bir değişken bildirir. Üç yolla bildirimi yazabilirsiniz:  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 Değişkeni `ridesBusToWork` değerini tutabilir `True`, değerini `False`, ya da hiç herhangi bir değer. İlk varsayılan değeri, bu durumda bilgileri henüz bu kişinin elde edilmiş değil olduğundan anlamına gelebilir hiçbir değer hiç olduğu. Buna karşılık, `False` bilgi alınabilir ve kişi çalışmak için veri yolu ride değil anlamına gelebilir.  
  
 Boş değer atanabilir türleri ile değişkenleri ve özellikleri bildirme ve bir dizi null atanabilir bir tür öğelerin bildirebilirsiniz. Parametre olarak boş değer atanabilir türler ile yordamları bildirebilir ve boş değer atanabilir bir tür döndürebilirsiniz bir `Function` yordamı.  
  
 Boş değer atanabilir bir tür başvuru türünde bir dizi gibi oluşturamaz bir `String`, ya da bir sınıf. Temel alınan tür değeri türü olmalıdır. Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
## <a name="using-a-nullable-type-variable"></a>Boş değer atanabilir tür değişken kullanma  
 Boş değer atanabilir bir tür en önemli üyeleri olan kendi <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleri. Boş değer atanabilir türde bir değişken için <xref:System.Nullable%601.HasValue%2A> değişkeni tanımlı bir değer içerip içermediğini belirtir. Varsa <xref:System.Nullable%601.HasValue%2A> olan `True`, değerini okuyabilirsiniz <xref:System.Nullable%601.Value%2A>. Unutmayın her ikisi de <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> olan `ReadOnly` özellikleri.  
  
### <a name="default-values"></a>Varsayılan değerler  
 Bir değişken null atanabilir bir tür ile bildirirken kendi <xref:System.Nullable%601.HasValue%2A> özelliğinin varsayılan değeri `False`. Başka bir deyişle, varsayılan olarak tanımlanan değeri, temel alınan değer türü varsayılan değeri yerine değişkeni yok. Aşağıdaki örnekte, değişken `numberOfChildren` başlangıçta tanımlanan değeri, varsayılan değerini rağmen yok `Integer` türü: 0.  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 Null değeri tanımlanmamış veya bilinmeyen bir değer belirtmek kullanışlıdır. Varsa `numberOfChildren` olarak bildirilmiş `Integer`, bilgileri şu anda kullanılamıyor gösterebilir herhangi bir değer olacaktır.  
  
### <a name="storing-values"></a>Değerlerini depolama  
 Bir değeri bir değişken veya boş değer atanabilir bir tür özelliğine normal şekilde depolayın. Aşağıdaki örnek değişkene değer atayan `numberOfChildren` önceki örnekte bildirilmedi.  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 Bir değişken veya boş değer atanabilir bir tür özelliği tanımlı bir değer içeriyorsa, atanmış bir değere sahip değil, ilk durumuna geri dönmek neden olabilir. Değişken ya da özelliğini ayarlayarak bunu `Nothing`, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  Atayabilirsiniz rağmen `Nothing` bir boş değer atanabilir türde bir değişkene için test edemiyor `Nothing` eşittir işaretinden kullanarak. Eşittir işareti kullanan karşılaştırma `someVar = Nothing`, her zaman değerlendiren `Nothing`. Değişkenin sınayabilirsiniz <xref:System.Nullable%601.HasValue%2A> özelliği için `False`, veya test kullanarak `Is` veya `IsNot` işleci.  
  
### <a name="retrieving-values"></a>Değerleri alma  
 Boş değer atanabilir türde bir değişken değerini almak için önce sınamalısınız kendi <xref:System.Nullable%601.HasValue%2A> bir değer aldığından emin olmak için özellik. Değerini okumaya çalışırsanız, <xref:System.Nullable%601.HasValue%2A> olan `False`, Visual Basic oluşturur bir <xref:System.InvalidOperationException> özel durum. Değişkeni okumak için önerilen yöntem aşağıdaki örnekte `numberOfChildren` önceki örneklerin.  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a>Boş değer atanabilir türler karşılaştırma  
 Boş değer atanabilir zaman `Boolean` değişkenleri Boolean ifadelerinde kullanılıyorsa, sonucu olabilir `True`, `False`, veya `Nothing`. Gerçekte tablodur aşağıdaki `And` ve `Or`. Çünkü `b1` ve `b2` artık üç olası değerlere sahip değerlendirmek için dokuz birleşim vardır.  
  
|B1|B2|B1 ve b2|B1 veya b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 Ne zaman bir Boolean değişkeni veya ifade değeri `Nothing`, ne olduğunu `true` ya da `false`. Aşağıdaki örnek göz önünde bulundurun.  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 Bu örnekte, `b1 And b2` değerlendiren `Nothing`. Sonuç olarak, `Else` yan tümcesi her yürütüldüğünde `If` deyimi ve çıktı aşağıdaki gibidir:  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` ve `OrElse`, kullanım, değerlendirme, kısa devre oluşturur gerekir değerlendirmek kendi ikinci işlenen ilk olarak değerlendirildiğinde `Nothing`.  
  
## <a name="propagation"></a>Yayma  
 Birini veya her ikisini bir aritmetik, karşılaştırma, SHIFT veya türü işlem işlenenleri boş değer atanabilir işleminin sonucu da null ise. Her iki işlenen olmayan değerler içeriyorsa `Nothing`, ne değilmiş gibi işlem işlenenler temel değerlerine gerçekleştirilir null atanabilir bir tür. Aşağıdaki örnekte, değişkenleri `compare1` ve `sum1` örtülü olarak yazılan. Fare işaretçisini üzerine getirdiğinizde, derleyici boş değer atanabilir türler ikisinin için oluşturur olduğunu görürsünüz.  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 Bir veya iki işlenen değeri varsa `Nothing`, sonucu olacaktır `Nothing`.  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a>Verilerle boş değer atanabilir türleri kullanma  
 Bir veritabanı, boş değer atanabilir türler kullanmak için en önemli basamak biridir. Tüm veritabanı nesneleri şu anda boş değer atanabilir türler destekler, ancak Tablo Tasarımcısı tarafından oluşturulan bağdaştırıcıları yapın. "Boş değer atanabilir türler için TableAdapter destek" bölümüne bakın [TableAdapter genel bakışı](/visualstudio/data-tools/tableadapter-overview).
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [Boş Değer Atanabilir Tipleri Kullanma](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [TableAdapter genel bakış](/visualstudio/data-tools/tableadapter-overview)  
 [If İşleci](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Is İşleci](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot İşleci](../../../../visual-basic/language-reference/operators/isnot-operator.md)
