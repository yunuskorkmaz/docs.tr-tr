---
title: Tip dinamiği kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: c5ac5b3692266010f0be8672ef744baaa32e6a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711863"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Tür dinamiği kullanma (C# Programlama Kılavuzu)

C# 4 yeni bir `dynamic`tür tanıttı. Tür statik bir türdür, ancak `dynamic` bir tür nesnesi statik tür denetimini atlar. Çoğu durumda, türü `object`var gibi çalışır. Derleme zamanında, herhangi bir işlemi destekleyecek `dynamic` şekilde yazılan bir öğe. Bu nedenle, nesnenin değerini com API'sinden mi, IronPython gibi dinamik bir dilden mi, HTML Belge Nesnesi Modeli'nden (DOM) veya programdaki başka bir yerden mi aldığı konusunda endişelenmenize gerek yoktur. Ancak, kod geçerli değilse, hatalar çalışma zamanında yakalanır.

Örneğin, aşağıdaki koddaki örnek yönteminin `exampleMethod1` yalnızca bir parametresi varsa, derleyici yönteme `ec.exampleMethod1(10, 4)`yapılan ilk çağrının, iki bağımsız değişken içerdiğinden geçerli olmadığını kabul eder. Çağrı derleyici hatasına neden olur. Yönteme ikinci çağrı, `dynamic_ec.exampleMethod1(10, 4)`, türü `dynamic_ec` olduğu `dynamic`için derleyici tarafından denetlenmez. Bu nedenle, hiçbir derleyici hatası bildirilir. Ancak, hata süresiz bildirim kaçış değil. Çalışma zamanında yakalanır ve çalışma zamanı özel bir özel durum neden olur.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Bu örneklerde derleyicinin rolü, her ifadenin nesne ye veya ifadeye ne yapmayı önerdiği `dynamic`ne olduğu yla ilgili bilgileri bir araya getirmektir. Çalışma zamanında, depolanan bilgiler incelenir ve geçerli olmayan herhangi bir deyim çalışma zamanı özel bir özel durum neden olur.

En dinamik işlemlerin sonucu `dynamic`kendisidir. Örneğin, fare işaretçisini `testSum` aşağıdaki örnekte kullanımı üzerine dinlendirmek, IntelliSense türü **(yerel değişken) dinamik testSum**görüntüler.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Sonucun içermeyen `dynamic` işlemleri:

* Dönüşümler `dynamic` başka bir türe.
* Tür `dynamic`bağımsız değişkenleri içeren oluşturucu çağrıları.

Örneğin, aşağıdaki bildirimdeki `testInstance` türü `ExampleClass`, değil: `dynamic`

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Dönüşüm örnekleri aşağıdaki bölümde gösterilmiştir: "Dönüşümler."

## <a name="conversions"></a>Dönüşümler

Dinamik nesneler ve diğer türler arasındaki dönüşümler kolaydır. Bu, geliştiricinin dinamik ve dinamik olmayan davranışlar arasında geçiş yapabilmesini sağlar.

Herhangi bir nesne, aşağıdaki örneklerde gösterildiği gibi, dolaylı olarak dinamik türe dönüştürülebilir.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Tersine, örtülü dönüştürme dinamik tür `dynamic`herhangi bir ifade uygulanabilir.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Tip dinamiği bağımsız değişkenleri ile aşırı yükleme çözünürlüğü

Aşırı yük çözünürlüğü, bir yöntem çağrısındaki bağımsız değişkenlerden biri veya daha fazlası `dynamic`türe sahipse veya yöntem `dynamic`çağrısının alıcısı türdeyse, derleme zamanında değil, çalışma zamanında oluşur. Aşağıdaki örnekte, tek erişilebilir `exampleMethod2` yöntem bir dize bağımsız `d1` değişkeni almak için tanımlanmışsa, bağımsız değişken derleyici hatasına neden olmadığı için gönderme, ancak çalışma zamanı özel bir durum neden olur. Çalışma zamanı türü ve `d1` `int`bir dize `exampleMethod2` gerektirdiğinden, aşırı yükleme çözünürlüğü çalışma zamanında başarısız olur.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma süresi

Dinamik dil çalışma süresi (DLR), .NET Framework 4'teki yeni bir API'dir. C#'daki `dynamic` türü destekleyen altyapıyı ve IronPython ve IronRuby gibi dinamik programlama dillerinin uygulanmasını sağlar. DLR hakkında daha fazla bilgi için [Dinamik Dil Çalışma Süresine Genel Bakış'a](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)bakın.

## <a name="com-interop"></a>COM birlikte çalışma

C# 4, Office Automation API'leri gibi COM API'leri ile birlikte çalışma deneyimini geliştiren çeşitli özellikler içerir. Geliştirmeler arasında `dynamic` tür kullanımı ve adlı [ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md)vardır.

Birçok COM yöntemi, türleri ' olarak `object`atlayarak bağımsız değişken türlerinde ve return türünde varyasyonsağlar. Bu, C#'da güçlü bir şekilde yazılan değişkenlerle koordine olmak için değerlerin açık bir şekilde döküme çevrilmesi gerekti. [-link (C# Derleyici Seçenekleri)](../../language-reference/compiler-options/link-compiler-option.md) seçeneğini kullanarak derlerseniz, `dynamic` türün girişi COM `object` imzalarında meydana gelen oluşumları türde `dynamic`yitiyormuş gibi ele alabilmenizi ve bu nedenle dökümün büyük bir kısmını önlemenizi sağlar. Örneğin, aşağıdaki ifadeler, Microsoft Office Excel elektronik tablosundaki bir `dynamic` hücreye türüyle ve türü olmayan bir hücreye nasıl eriştinsinizin `dynamic` tam tersidir.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dinamik](../../language-reference/builtin-types/reference-types.md)|`dynamic` Anahtar kelimenin kullanımını açıklar.|
|[Dinamik Dil Çalışma Süresine Genel Bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Ortak dil çalışma süresine (CLR) dinamik diller için bir dizi hizmet ekleyen bir çalışma zamanı ortamı olan DLR'ye genel bir bakış sağlar.|
|[Walkthrough: Dinamik Nesneler Oluşturma ve Kullanma](walkthrough-creating-and-using-dynamic-objects.md)|Özel dinamik bir nesne oluşturmak ve `IronPython` kitaplıkla erişen bir proje oluşturmak için adım adım yönergeler sağlar.|
|[Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](../interop/how-to-access-office-onterop-objects.md)|Office API nesnelerine erişimi kolaylaştıran adlandırılmış `dynamic` ve isteğe bağlı bağımsız değişkenleri, türü ve diğer geliştirmeleri kullanan bir projeyi nasıl oluşturup oluşturabilirsiniz' u gösterir.|
