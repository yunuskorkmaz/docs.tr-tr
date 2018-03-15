---
title: "Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 396914e487bee0924c36bb1d7a0f28976f4ad354
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)
Tanımını bölme mümkündür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md), bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) veya iki veya daha fazla kaynak dosyalar üzerinde bir yöntem. Her kaynak dosya türü veya yöntemi tanımının bir bölüm içerir ve uygulamanın derlendiğinde tüm bölümleri birleştirilir.  
  
## <a name="partial-classes"></a>Kısmi sınıflar  
 Bir sınıf tanımı bölme arzu olduğunda bazı durumlar vardır:  
  
-   Büyük projeler üzerinde çalışırken, ayrı dosyalar üzerinde bir sınıf yayılmak birden çok programcıların üzerinde aynı anda çalışması olanak tanır.  
  
-   Otomatik olarak oluşturulan kaynağı ile çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan sınıfına kod eklenebilir. Windows Forms, Web hizmeti sarmalayıcı kodu ve benzeri oluşturduğunda, visual Studio bu yaklaşımı kullanır. Visual Studio tarafından oluşturulan dosyasını değiştirmek zorunda kalmadan bu sınıfları kullanan kodu oluşturabilirsiniz.  
  
-   Bir sınıf tanımı bölmek için kullanın [kısmi](../../../csharp/language-reference/keywords/partial-type.md) anahtar sözcüğü değiştiricisi, aşağıda gösterildiği gibi:  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` Arabirimi ad alanında tanımlanabilir veya anahtar sözcüğü sınıf, yapı, diğer parçalarını gösterir. Tüm bölümleri kullanmalısınız `partial` anahtar sözcüğü. Tüm bölümleri adresinde son türü oluşturmak için zaman derleyin. Tüm bölümleri aynı erişilebilirlik gibi olmalıdır `public`, `private`ve benzeri.  
  
 Herhangi bir bölümünü soyut bildirilirse, tüm türünü soyut olarak değerlendirilir. Tam tür korumalı olarak kabul edilip sonra herhangi bir bölümünü korumalı, bildirilirse. Herhangi bir bölümünü bir taban türü bildirirse, tüm türü o sınıfın devralır.  
  
 Bir taban sınıfı belirtin tüm bölümleri kabul etmeniz gerekir, ancak bir taban sınıf atlayın bölümleri hala temel türü devralır. Son türü tarafından tüm kısmi bildirimleri listelenen tüm arabirimlerini uygular ve parça farklı temel arabirimleri belirtebilirsiniz. Herhangi bir sınıf, yapısı veya kısmi tanımında bildirilen arabirim üyeleri için diğer tüm bölümleri kullanılabilir. Son türü tüm bölümleri derleme zamanında birleşimidir.  
  
> [!NOTE]
>  `partial` Değiştiricisi temsilci ya da numaralandırması bildirimlerinde kullanılabilir değil.  
  
 Aşağıdaki örnek, içinde iç içe türü kısmi olmasa bile, iç içe geçmiş türler kendisini kısmi, olabileceğini gösterir.  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 Derleme zamanında kısmi tür tanımları özniteliklerini birleştirilir. Örneğin, aşağıdaki bildirimlerini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Bunlar aşağıdaki bildirimi eşdeğerdir:  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 Aşağıdaki tüm kısmi türü tanımları birleştirilir:  
  
-   XML açıklamaları  
  
-   arabirimler  
  
-   genel tür parametre öznitelikleri  
  
-   class öznitelikleri  
  
-   üyeler  
  
 Örneğin, aşağıdaki bildirimlerini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Bunlar aşağıdaki bildirimi eşdeğerdir:  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>Kısıtlamalar  
 Parçalı sınıf tanımları ile çalışırken izlemek için çeşitli kurallar şunlardır:  
  
-   Aynı türde bölümleri olma amacını tüm kısmi tür tanımları ile değiştirilmelidir `partial`. Örneğin, aşağıdaki sınıf bildirimleri bir hata oluştur:  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` Değiştiricisi yalnızca hemen önce anahtar sözcükleri görünür `class`, `struct`, veya `interface`.  
  
-   Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş kısmi türler kısmi türü tanımlarına izin verilir:  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Aynı türde bölümleri olma amacını tüm kısmi tür tanımları aynı bütünleştirilmiş kodda ve aynı Modülü (.exe veya .dll dosyası) tanımlanması gerekir. Kısmi tanımları birden fazla modülü yayılamaz.  
  
-   Genel tür parametreleri ve sınıf adı tüm kısmi türü tanımlarını eşleşmesi gerekir. Genel türler kısmi olabilir. Her kısmi bildirimi aynı parametre adları aynı sırada kullanmanız gerekir.  
  
-   Kısmi tür tanımı aşağıdaki anahtar sözcükler isteğe bağlıdır, ancak varsa bir kısmi tür tanımı, aynı türde başka bir kısmi tanımında belirtilen anahtar sözcükleri çakışmamalıdır:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   taban sınıfı  
  
    -   [Yeni](../../../csharp/language-reference/keywords/new.md) değiştiricisi (iç içe geçmiş parça)  
  
    -   Genel kısıtlamalar  
  
         Daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, alanları ve sınıf `CoOrds`, bir parçalı sınıf tanımı ve üye bildirilen `PrintCoOrds`, başka bir parçalı sınıf tanımı'nda bildirilir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, ayrıca kısmi yapıları ve arabirimleri geliştirebilirsiniz olduğunu gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>Kısmi Yöntemler  
 Kısmi bir yöntem, kısmi sınıfta veya yapı içerebilir. Sınıfının bir parçası yönteminin imza içeriyor. İsteğe bağlı bir uygulama aynı bölüme veya başka bir parçası tanımlanabilir. Uygulama sağlanmazsa, derleme zamanında yöntemi ve yöntemine yönelik tüm çağrılar kaldırılır.  
  
 Kısmi yöntemler, bir olaya benzer bir yöntemi tanımlamak uygulayan bir sınıf bir parçası olarak etkinleştirin. Bir sınıf parçası uygulayan yöntemi veya uygulamak karar verebilirsiniz. Yöntem uygulanmadı sonra yöntemi derleyici kaldırır imza ve yöntemine yönelik tüm çağrılar. Değerlendirme çağrıları bağımsız değişkenleri oluşacak sonuçları dahil olmak üzere yöntem çağrıları çalışma zamanında bir etkisi yoktur. Bu nedenle, uygulama sağlanmadı olsa bile bir parçalı sınıf kodda serbestçe kısmi bir yöntemi kullanabilirsiniz. Yöntemi çağrıldı ancak uygulanmadı içeriyorsa hiçbir derleme zamanı ya da çalışma zamanı hataları oluşur.  
  
 Kısmi yöntemler oluşturulan kod özelleştirmek için bir yol olarak özellikle yararlıdır. Bir yöntem adı için izin ve böylece kodu oluşturulan ayrılmasını imza yöntemini çağırabilir ancak geliştirici yöntemi uygulamak karar verebilirsiniz. Çok parçalı sınıflar gibi bir kod Oluşturucu tarafından oluşturulan kodu ve birlikte çalışma zamanı maliyetleri çalışacak biçimde İnsan geliştirici tarafından oluşturulan kodu kısmi yöntemler etkinleştirin.  
  
 Kısmi yöntem bildirimi iki bölümden oluşur: tanımı ve uygulama. Bunlar, ayrı bir parçalı sınıf bölümlerini ya da aynı bölümü olabilir. Hiçbir uygulama bildirimi yok sonra derleyici hemen her iki tanımlama en iyi duruma getirir ve yöntemine yönelik tüm çağrılar bildirimi.  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Kısmi yöntem bildirimleri bağlamsal anahtar sözcüğü ile başlamalıdır [kısmi](../../../csharp/language-reference/keywords/partial-type.md) ve yöntem döndürmelidir [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Kısmi yöntemler olabilir [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) veya [ref](../../../csharp/language-reference/keywords/ref.md) ama [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.  
  
-   Kısmi yöntemler şunlardır örtük olarak [özel](../../../csharp/language-reference/keywords/private.md), ve bu nedenle olamaz [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Kısmi yöntemler olamaz [extern](../../../csharp/language-reference/keywords/extern.md), çünkü gövdesi varlığını bunlar tanımlama uygulama ya da olup olmadığını belirler.  
  
-   Kısmi yöntemler olabilir [statik](../../../csharp/language-reference/keywords/static.md) ve [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) değiştiricileri.  
  
-   Kısmi yöntemler genel olabilir. Kısıtlamaları tanımlayan kısmi yöntemi bildirimde yerleştirilir ve uygulayan bir isteğe bağlı olarak yinelenebilir. Parametre adları parametre ve türünü tanımlayan bir olduğu gibi uygulama bildiriminde aynı olması gerekmez.  
  
-   Yapabileceğiniz bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) tanımlanan ve uygulanan bir kısmi yöntemi, ancak yalnızca tanımlı bir kısmi yöntem değil.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [partial (Tür)](../../../csharp/language-reference/keywords/partial-type.md)
