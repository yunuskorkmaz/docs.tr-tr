---
title: Kısmi sınıflar ve yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 7e91d77393c4d2980cce73a92589b752124e8077
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965208"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)
Tanımı bölmek mümkündür bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapı](../../../csharp/language-reference/keywords/struct.md)e [arabirimi](../../../csharp/language-reference/keywords/interface.md) ya da iki veya daha fazla kaynak dosyalar üzerinde bir yöntem. Her kaynak dosyası türü veya yönteminde tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçaları bir araya getirilir.  
  
## <a name="partial-classes"></a>Kısmi sınıflar  
 Bir sınıf tanımı bölmeyi tercih edilir, birkaç durum vardır:  
  
-   Büyük projeler üzerinde çalışırken, bir sınıf ayrı dosyalar yayılmasını üzerinde aynı anda çalışmak birden çok programcıları sağlar.  
  
-   Otomatik olarak oluşturulan kaynak ile çalışırken kod sınıfa kaynak dosyası yeniden oluşturmak zorunda kalmadan eklenebilir. Visual Studio, Windows Forms, Web hizmeti sarmalayıcı kodu ve benzeri oluşturduğunda, bu yaklaşımı kullanır. Bu sınıflar, Visual Studio tarafından oluşturulan dosya değiştirmek zorunda kalmadan kullanan kodu oluşturabilirsiniz.  
  
-   Bir sınıf tanımı bölmek için kullanın [kısmi](../../../csharp/language-reference/keywords/partial-type.md) burada gösterildiği gibi anahtar sözcüğü değiştiricisi:  
  
 [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]  
  
 `partial` Anahtar sözcüğü, sınıf, yapı, diğer bölümlerini gösterir veya arabirimi ad alanı içinde tanımlanabilir. Tüm parçaları kullanmalısınız `partial` anahtar sözcüğü. Tüm parçaları kullanılabilir son türü oluşturmak için zaman derleyin. Tüm parçaları gibi aynı erişilebilirliği olmalıdır `public`, `private`ve benzeri.  
  
 Herhangi bir bölümü soyut olarak bildirilirse, tüm türü soyut olarak değerlendirilir. Tüm tür korumalı olarak kabul edilip sonra herhangi bir bölümü sealed bildirilmişse. Herhangi bir bölümü bir taban türü bildirirse, tüm tür o sınıf devralır.  
  
 Bir taban sınıfı belirtin tüm bölümleri kabul etmeniz gerekir, ancak bir temel sınıf atlayın parçaları temel tür hala devralır. Son türü kısmi bildirimleri listelenen tüm arabirimlerini uygular ve bölümleri farklı temel arabirimleri belirtebilirsiniz. Herhangi bir sınıf, yapı veya arabirim üyeleri bir kısmi tanımda'olarak bildirilen tüm diğer bölümleri için kullanılabilir. Tüm parçaları birleşimi derleme zamanında son türüdür.  
  
> [!NOTE]
>  `partial` Değiştiricisi, temsilci veya sabit listesi bildirimlerinde kullanılabilir değil.  
  
 Aşağıdaki örnek, içinde iç içe türü kısmi olmasa bile, iç içe geçmiş türler kendisini kısmi, olabileceğini gösterir.  
  
 [!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]  
  
 Derleme zamanında öznitelikleri kısmi türü tanımları birleştirilir. Örneğin, aşağıdaki bildirimleri dikkate alın:  
  
 [!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]  
  
 Bunlar, aşağıdaki bildirimi eşdeğerdir:  
  
 [!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]  
  
 Aşağıdaki tüm kısmi türü tanımları birleştirilir:  
  
-   XML açıklamaları  
  
-   arabirimler  
  
-   genel tür parametre öznitelikleri  
  
-   class öznitelikleri  
  
-   üyeler  
  
 Örneğin, aşağıdaki bildirimleri dikkate alın:  
  
 [!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]  
  
 Bunlar, aşağıdaki bildirimi eşdeğerdir:  
  
 [!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]  
  
### <a name="restrictions"></a>Kısıtlamalar  
 Kısmi sınıf tanımları ile çalışırken yordamları izlemek için çeşitli kurallar şunlardır:  
  
-   Bölümleri aynı türde olacak şekilde tasarlanmış tüm kısmi tür tanımları ile değiştirilmelidir `partial`. Örneğin, aşağıdaki sınıf bildirimleri hata oluşturur:  
  
     [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]  
  
-   `partial` Değiştiricisi hemen önce anahtar sözcükler yalnızca görüntülenebilir `class`, `struct`, veya `interface`.  
  
-   Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş kısmi türler kısmi türü tanımlarında izin verilir:  
  
     [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]  
  
-   Tüm kısmi tür tanımlarını bölümleri aynı türde olacak şekilde tasarlanmış, aynı derleme ve aynı modülde (.exe veya .dll dosyası) tanımlanmış olması gerekir. Kısmi tanımlar, birden çok modül yayılamaz.  
  
-   Tüm kısmi tür tanımları, genel tür parametreleri ve sınıf adı eşleşmelidir. Genel türler, kısmi olabilir. Her bir kısmi bildirimi aynı sırada aynı parametre adları kullanmanız gerekir.  
  
-   Aşağıdaki anahtar sözcükler kısmi tür tanımında isteğe bağlıdır, ancak bir kısmi tür tanımı varsa, aynı türde başka bir kısmi tanımında belirtilen anahtar sözcüklerle çakışmamalıdır:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   taban sınıfı  
  
    -   [Yeni](../../../csharp/language-reference/keywords/new.md) değiştirici (iç içe geçmiş parça)  
  
    -   Genel sınırlamalar  
  
         Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, alanları ve sınıf oluşturucusunun `Coords`, bir kısmi sınıf tanımı ve üye bildirilir `PrintCoords`, başka bir kısmi sınıf tanımında bildirilir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, ayrıca kısmi yapılar ve arabirimler geliştirebilirsiniz olduğunu gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]  
  
## <a name="partial-methods"></a>Kısmi Yöntemler  
 Kısmi bir yöntemin kısmi bir sınıf veya yapı içerebilir. Bir sınıfın parçası yöntem imzası içerir. İsteğe bağlı bir uygulama aynı bölüm veya başka bir parçası tanımlanabilir. Uygulama sağlanmazsa, derleme zamanında yöntemi ve yöntemine yönelik tüm çağrılar kaldırılır.  
  
 Kısmi yöntemler, bir olay için benzer bir yöntemi tanımlamak bir parçası olan bir sınıf uygulayan etkinleştirin. Uygulayan bir sınıfın parçası, yöntemi veya uygulamamaya karar verebilirsiniz. Yöntem uygulanmadı sonra derleyici yöntemi kaldırır imzası ve yöntemine yapılan tüm çağrıları. Değerlendirme çağrılarındaki bağımsız değişkenler, ortaya çıkabilecek tüm sonuçları dahil olmak üzere, yöntem çağrıları çalışma zamanında bir etkisi yoktur. Bu nedenle, uygulama sağlanmazsa olsa bile kısmi sınıftaki herhangi bir kod serbestçe kısmi bir yöntemi kullanabilirsiniz. Yöntemi çağrılır ancak uygulanmadı hiçbir derleme zamanı veya çalışma zamanı hataları neden olur.  
  
 Kısmi yöntemler bir şekilde oluşturulan kod özelleştirmek için özellikle yararlıdır. İçin bir yöntem adı sağlarlar ve böylece kod oluşturulan ayrılması için imza yöntemi çağırabilirsiniz ancak geliştirici yöntemi uygulamak karar verebilirsiniz. Çok parçalı sınıflar gibi bir kod Oluşturucu tarafından oluşturulan kodu ve çalışma zamanı maliyetleri birlikte çalışmak için bir insan geliştirici tarafından oluşturulan kodu kısmi yöntemler etkinleştirin.  
  
 Kısmi yöntem bildiriminde iki bölümden oluşur: tanımı ve uygulaması. Bunlar ayrı bölümlerini kısmi bir sınıf ya da aynı bölümü olabilir. Hiçbir uygulama bildirimi yok sonra derleyici, hemen her iki tanımlama iyileştirir ve yöntemine yönelik tüm çağrılar bildirimi.  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Kısmi yöntem bildiriminin bağlamsal anahtar sözcüğüyle başlamalı [kısmi](../../../csharp/language-reference/keywords/partial-type.md) ve yöntem döndürmelidir [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Kısmi yöntemler olabilir [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) veya [ref](../../../csharp/language-reference/keywords/ref.md) ama [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.  
  
-   Kısmi yöntemler dolaylı olarak olan [özel](../../../csharp/language-reference/keywords/private.md), ve bu nedenle olamaz [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Kısmi yöntemler olamaz [extern](../../../csharp/language-reference/keywords/extern.md), Varlık gövdesi bunlar tanımlama uygulama mı olduğunu belirler.  
  
-   Kısmi yöntemler olabilir [statik](../../../csharp/language-reference/keywords/static.md) ve [güvenli](../../../csharp/language-reference/keywords/unsafe.md) değiştiriciler.  
  
-   Kısmi yöntemler, genel olabilir. Kısıtlamaları tanımlayan kısmi yöntem bildiriminde yerleştirilir ve isteğe bağlı olarak uygulayan bir yinelenebilir. Parametre adları parametre ve türü tanımlayan bir olduğu gibi uygulama bildiriminde aynı olması gerekmez.  
  
-   Yapabileceğiniz bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) tanımlanan ve uygulanan kısmi bir yöntem, ancak yalnızca tanımlı bir kısmi yöntem değil.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [kısmi türlerinden](~/_csharplang/spec/classes.md#partial-types) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
- [partial (Tür)](../../../csharp/language-reference/keywords/partial-type.md)
