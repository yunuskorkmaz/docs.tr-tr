---
title: Tür dinamik C# programlama kılavuzunu kullanma
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 4141c64ff6dbbec60b53a41862a4273df6ef51ab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588354"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Dinamik tür kullanımı (C# Programlama Kılavuzu)

C#4 yeni bir tür tanıtır, `dynamic`. Tür statik bir türdür, ancak türünde `dynamic` bir nesne statik tür denetimini atlar. Çoğu durumda, bu, türü `object`gibi çalışır. Derleme zamanında, olarak `dynamic` yazılan bir öğe herhangi bir işlemi destekleyecek şekilde varsayılır. Bu nedenle, nesnenin değerini bir COM API 'sinden, IronPython gibi dinamik bir dilden, HTML Belge Nesne Modeli (DOM), yansımasından veya programdaki herhangi bir yerden alıp ulaşmamasından endişe etmeniz gerekmez. Ancak, kod geçerli değilse, hatalar çalışma zamanında yakalanmalıdır.

Örneğin, aşağıdaki kodda bulunan örnek `exampleMethod1` yönteminin yalnızca bir parametresi varsa, derleyici iki bağımsız değişken içerdiğinden, `ec.exampleMethod1(10, 4)`yöntemin ilk çağrısının geçerli olmadığını algılar. Çağrı, bir derleyici hatasına neden olur. Öğesinin `dynamic_ec.exampleMethod1(10, 4)` türü`dynamic_ec` olduğundan,yöntemiiçinikinciçağrı`dynamic`derleyici tarafından denetlenmez. Bu nedenle, hiçbir derleyici hatası bildirilmemiştir. Ancak, hata süresiz olarak çıkış yapmaz. Çalışma zamanında yakalanır ve bir çalışma zamanı özel durumuna neden olur.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Bu örneklerde derleyicinin rolü, her bir deyimin, olarak `dynamic`yazılan nesne veya ifade için hangi şekilde önerdikleridir hakkındaki bilgileri birlikte paketlemenize olanak sağlar. Çalışma zamanında, depolanan bilgiler incelenir ve geçerli olmayan herhangi bir ifade çalışma zamanı özel durumuna neden olur.

Çoğu dinamik işlemin sonucu kendi kendisidir `dynamic`. Örneğin, fare işaretçisini aşağıdaki örnekte öğesinin `testSum` kullanımı üzerine getirdiğinizde, IntelliSense türü **(yerel değişken) dinamik testsum**' ı görüntüler.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Sonucun `dynamic` içermediği işlemler:

* ' Den `dynamic` başka bir türe dönüşümler.
* Türündeki `dynamic`bağımsız değişkenleri içeren Oluşturucu çağrıları.

Örneğin, aşağıdaki `testInstance` `ExampleClass`bildirimde türü değildir `dynamic`:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Dönüştürme örnekleri aşağıdaki "Dönüşümler" bölümünde gösterilmiştir.

## <a name="conversions"></a>Dönüşümler

Dinamik nesneler ve diğer türler arasındaki dönüştürmeler kolaydır. Bu, geliştiricinin dinamik ve dinamik olmayan davranış arasında geçiş yapmasına olanak sağlar.

Aşağıdaki örneklerde gösterildiği gibi, herhangi bir nesne dinamik türe örtük olarak dönüştürülebilir.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Buna karşılık örtük bir dönüştürme, türünde `dynamic`herhangi bir ifadeye dinamik olarak uygulanabilir.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Dinamik türdeki bağımsız değişkenlerle aşırı yükleme çözümlemesi

Bir yöntem çağrısında bir veya daha fazla bağımsız değişken türü `dynamic`varsa veya yöntem çağrısının alıcısı tür `dynamic`ise, yükleme çözümü derleme zamanı yerine çalışma zamanında gerçekleşir. Aşağıdaki örnekte, tek bir dize bağımsız değişkeni almak `exampleMethod2` için yalnızca erişilebilir Yöntem tanımlanmışsa, bağımsız değişken olarak gönderme `d1` bir derleyici hatasına neden olmaz, ancak çalışma zamanı özel durumuna neden olur. Çalışma zamanı türü `d1` olduğu `int`ve `exampleMethod2` bir dize gerektirdiğinden aşırı yükleme çözümlemesi çalışma zamanında başarısız olur.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma zamanı

Dinamik dil çalışma zamanı (DLR) .NET Framework 4 ' te yeni bir API 'dir. İçindeki `dynamic` C#türü destekleyen altyapıyı ve ayrıca IronPython ve IronRuby gibi dinamik programlama dillerinin uygulanmasını sağlar. DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM birlikte çalışma

C#4, Office Otomasyonu API 'leri gibi COM API 'lerle birlikte çalışma deneyimini geliştiren çeşitli özellikler içerir. Geliştirmeler arasında, `dynamic` türünün ve [adlandırılmış ve isteğe bağlı bağımsız değişkenlerin](../classes-and-structs/named-and-optional-arguments.md)kullanımı vardır.

Birçok COM yöntemi, türleri olarak `object`tanımlayarak bağımsız değişken türlerinde ve dönüş türünde değişimler için izin verir. Bu, ' deki kesin olarak belirlenmiş değişkenlerle koordine etmek için değerlerin açık bir şekilde C#çevrim kümesini gerektiren bir [/Link (C# derleyici seçenekleri)](../../language-reference/compiler-options/link-compiler-option.md) seçeneğini kullanarak derlerseniz, `dynamic` türün tanıtımı com `object` imzalarındaki oluşumlarını, türü `dynamic`gibi kabul etmenizi sağlar ve bu nedenle atama. Örneğin, aşağıdaki deyimler Microsoft Office Excel elektronik `dynamic` tablosundaki bir hücreye türü ve `dynamic` türü olmadan nasıl erişirsiniz.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[dynamic](../../language-reference/keywords/dynamic.md)|`dynamic` Anahtar sözcüğünün kullanımını açıklar.|
|[Dinamik Dil Çalışma Zamanına Genel Bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Ortak dil çalışma zamanına (CLR) dinamik diller için bir hizmet kümesi ekleyen bir çalışma zamanı ortamı olan DLR 'ye genel bir bakış sağlar.|
|[İzlenecek yol: Dinamik nesneler oluşturma ve kullanma](walkthrough-creating-and-using-dynamic-objects.md)|Özel dinamik nesne oluşturmak ve bir `IronPython` kitaplığa erişen proje oluşturmak için adım adım yönergeler sağlar.|
|[Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin](../interop/how-to-access-office-onterop-objects.md)|Adlandırılmış ve isteğe bağlı bağımsız değişkenleri, `dynamic` türü ve Office API nesnelerine erişimi kolaylaştıran diğer geliştirmeleri kullanan bir projenin nasıl oluşturulacağını gösterir.|
