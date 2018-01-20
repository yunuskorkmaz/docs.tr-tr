---
title: "Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4c57efa4027af5dd6b0476eb65845a39fc0b691
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]adlandırılmış ve isteğe bağlı bağımsız değişkenler tanıtır. *Bağımsız değişkenler adlı* , belirli bir parametre için bir bağımsız değişken bağımsız değişken parametre adı yerine parametre listesinde parametrenin konumu ile ilişkilendirerek belirtmenize olanak verir. *İsteğe bağlı bağımsız değişkenler* bazı parametreler için bağımsız değişken atlayın olanak sağlar. Her iki tekniği yöntemleri, dizin oluşturucular, Oluşturucular ve temsilciler ile kullanılabilir.  
  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişken bağımsız değişken listesi, parametre listesi görünme sırasını değerlendirilir.  
  
 Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, yalnızca birkaç parametre isteğe bağlı parametreler listesinden için bağımsız değişkenleri eklemek etkinleştirin. Bu özelliği COM arabirimleri gibi Microsoft Office Otomasyon API çağrıları büyük ölçüde kolaylaştırır.  
  
## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler  
 Adlandırılmış bağımsız değişkenler gereken anımsaması veya çağrılan yöntem parametre listesi parametrelerinde sırasını bakmak için gelen boş. Her değişken için parametresi tarafından parametre adı belirtilebilir. Örneğin, sipariş ayrıntılarını yazdırır bir işlev (gibi satıcı adı, sipariş numarası & ürün adı) standart biçiminde bağımsız değişkenleri sıralamasında, işlev tarafından tanımlanan gönderen tarafından çağrılabilir.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Parametreler sırası hatırlamıyorsanız, ancak adlarını bilmeniz bağımsız değişkenler herhangi bir sırada gönderebilirsiniz.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Adlandırılmış bağımsız değişkenler ne her bağımsız değişkeni temsil eden belirleyerek kodunuzun okunabilirliğini de geliştirir. Aşağıdaki örnek yönteminde `sellerName` null veya boşluk olamaz. Her ikisi de olarak `sellerName` ve `productName` dize türleri, bağımsız değişkenleri konuma göre göndermek yerine, iki belirsizliğini ortadan kaldırmak ve kod okuyan herkes için karışıklığı azaltmak için adlandırılmış bağımsız değişkenler kullanılacak mantıklıdır.
  
 Bağımsız değişkenler, konumsal bağımsız değişkenlerle birlikte kullanıldığında adlı, geçerli olan sürece 

- Bunlar konumsal tüm bağımsız değişkenleri tarafından izlenmeyen veya

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _C# ile 7.2 Başlangıç_, doğru konumda kullanılırlar. Parametre aşağıdaki örnekte `orderNum` doğru konumda olsa da açıkça adlı değil.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Ancak, sipariş adlandırılmış bağımsız değişkenler konumsal değişkenleriyle ardından varsa geçersizdir.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bu bölümde bazı ek olanları birlikte örneklerinden uygular.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler  
 Yöntemi, oluşturucusu, dizin oluşturucu veya temsilci tanımını parametrelerini gerekli veya isteğe bağlı oldukları belirtebilirsiniz. Tüm çağrısı tüm gerekli parametreleri için bağımsız değişkenleri belirtmeniz gerekir, ancak isteğe bağlı parametreler için bağımsız değişken atlayabilirsiniz.  
  
 Her isteğe bağlı bir parametre kendi tanımının bir parçası olarak varsayılan bir değeri yok. Bu parametre için bağımsız değişken gönderilirse, varsayılan değer kullanılır. Varsayılan değer ifadelerin aşağıdaki türlerden biri olmalıdır:  
  
-   bir sabit ifadesine;  
  
-   bir ifade formun `new ValType()`, burada `ValType` olduğu gibi bir değer türü bir [enum](../../../csharp/language-reference/keywords/enum.md) veya [yapısı](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   bir ifade formun [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), burada `ValType` değer türü değil.  
  
 İsteğe bağlı parametreler parametre listesinin sonuna sonra gerekli parametreleri tanımlanır. Çağıran bir bağımsız değişken isteğe bağlı parametrelerden biri art arda herhangi biri için sağlıyorsa, tüm önceki isteğe bağlı parametreler için bağımsız değişken sağlamanız gerekir. Bağımsız değişken listesi boşluklar virgülle ayrılmış desteklenmez. Örneğin, aşağıdaki kodda yöntemi örneği `ExampleMethod` gerekli bir ve iki isteğe bağlı parametreler ile tanımlanır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 Aşağıdaki çağrı `ExampleMethod` üçüncü parametre için kullanılabilir ancak ikinci bağımsız değişken sağlanan derleyici hatası neden olur.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Ancak, üçüncü parametre adını biliyorsanız, görevi gerçekleştirmek için bir adlandırılmış bağımsız değişkeni kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense köşeli isteğe bağlı parametreler belirtmek için aşağıdaki çizimde gösterildiği gibi kullanır.  
  
 ![ExampleMethod yöntemi için IntelliSense Hızlı bilgileri. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
ExampleMethod isteğe bağlı parametreler  
  
> [!NOTE]
>  .NET kullanarak isteğe bağlı parametreler bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfı. `OptionalAttribute`Parametreler varsayılan bir değer gerektirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Oluşturucusu `ExampleClass` isteğe bağlı olduğu bir parametre içeriyor. Örnek yöntemi `ExampleMethod` gerekli parametresinin, `required`ve iki isteğe bağlı parametreler `optionalstr` ve `optionalint`. Kodda `Main` , yöntemi ve Oluşturucusu çağrılabilir farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>COM arabirimleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler desteğinin yanı sıra Office Automation API'leri gibi COM API'leri ile birlikte çalışabilirlik büyük ölçüde artırır.  
  
 Örneğin, [biçim](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) Microsoft Office Excel yönteminde [aralığı](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) arabirimi tümü isteğe bağlı yedi parametreleri sahiptir. Bu parametreler aşağıdaki çizimde gösterilmektedir.  
  
 ![Otomatik Biçim yöntemi için IntelliSense Hızlı bilgileri. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Otomatik Biçim parametreleri  
  
 C# 3.0 ve önceki sürümlerde, bağımsız değişken aşağıdaki örnekte gösterildiği gibi her bir parametreyi gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 Ancak, büyük ölçüde çağrısı basitleştirebilir `AutoFormat` C# 4. 0'sunulan adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanarak. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değeri değiştirmek istemiyorsanız, isteğe bağlı bir parametre için bağımsız değişken atlamak etkinleştirin. Aşağıdaki çağrısında yedi parametrelerden yalnızca birini kullanmak için bir değer belirtilirse.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Daha fazla bilgi ve örnekler için bkz: [nasıl yapılır: kullanım adlandırılmış ve isteğe bağlı bağımsız değişkenler Office programlama](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: erişim Office birlikte çalışma nesnelerine kullanarak olan Visual C# özellikleri tarafından](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanımını aşırı yükleme çözümü aşağıdaki şekillerde etkiler:  
  
-   Yöntemi, dizin oluşturucu veya oluşturucusu yürütme aday, tüm parametrelerinin isteğe bağlı olduğu veya karşılık gelen, adıyla veya konuma arama deyiminde tek bir bağımsız değişken ve bağımsız değişken parametre türüne dönüştürülebilir ise.  
  
-   Birden fazla aday bulunursa, tercih edilen dönüştürmeleri için aşırı çözümleme kurallarını açıkça belirtilen bağımsız değişkenler için uygulanır. İsteğe bağlı parametreleri belirtilmemişse bağımsız değişkenleri göz ardı edilir.  
  
-   İki aday eşit iyi olmasını nitelendirilmiştir, tercih değişkenleri çağrısında atlanmış isteğe bağlı parametreler yok bir aday gider. Daha az parametrelere sahip bir aday aşırı çözünürlük genel bir tercih sonucu budur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Dizin Oluşturucular Kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)
