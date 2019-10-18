---
title: Tür dinamik C# programlama kılavuzunu kullanma
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: aef64f538aecb0fc5dadec850020d7c01d02ccbd
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523542"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Dinamik tür kullanımı (C# Programlama Kılavuzu)

C#4 `dynamic` yeni bir tür tanıtır. Tür statik bir türdür, ancak `dynamic` türünde bir nesne statik tür denetimini atlar. Çoğu durumda, bu işlev `object` tür gibidir. Derleme zamanında, `dynamic` olarak yazılan bir öğe, herhangi bir işlemi desteklemeye yönelik olarak kabul edilir. Bu nedenle, nesnenin değerini bir COM API 'sinden, IronPython gibi dinamik bir dilden, HTML Belge Nesne Modeli (DOM), yansımasından veya programdaki herhangi bir yerden alıp ulaşmamasından endişe etmeniz gerekmez. Ancak, kod geçerli değilse, hatalar çalışma zamanında yakalanmalıdır.

Örneğin, aşağıdaki kodda `exampleMethod1` örnek yönteminin yalnızca bir parametresi varsa, derleyici iki bağımsız değişken içerdiğinden, `ec.exampleMethod1(10, 4)` yöntemine yapılan ilk çağrının geçerli olmadığını algılar. Çağrı, bir derleyici hatasına neden olur. @No__t_1 türü `dynamic` olduğundan, `dynamic_ec.exampleMethod1(10, 4)` metoduna yapılan ikinci çağrı derleyici tarafından denetlenmez. Bu nedenle, hiçbir derleyici hatası bildirilmemiştir. Ancak, hata süresiz olarak çıkış yapmaz. Çalışma zamanında yakalanır ve bir çalışma zamanı özel durumuna neden olur.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Bu örneklerde derleyicinin rolü, her bir deyimin `dynamic` olarak yazılan nesne veya ifade için hangi amaçla önerdikleridir hakkındaki bilgileri birlikte paketlemenize olanak sağlar. Çalışma zamanında, depolanan bilgiler incelenir ve geçerli olmayan herhangi bir ifade çalışma zamanı özel durumuna neden olur.

Çoğu dinamik işlemin sonucu `dynamic`. Örneğin, aşağıdaki örnekte fare işaretçisini `testSum` kullanımı üzerine getirdiğinizde, IntelliSense türü **(yerel değişken) dinamik testSum**' ı görüntüler.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Sonucun `dynamic` dahil olmadığı işlemler şunlardır:

* @No__t_0 dönüştürme işlemleri başka bir türe.
* @No__t_0 türünde bağımsız değişkenler içeren Oluşturucu çağrıları.

Örneğin, aşağıdaki bildirimde `testInstance` türü `dynamic` değil `ExampleClass`.

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Dönüştürme örnekleri aşağıdaki "Dönüşümler" bölümünde gösterilmiştir.

## <a name="conversions"></a>Dönüşümler

Dinamik nesneler ve diğer türler arasındaki dönüştürmeler kolaydır. Bu, geliştiricinin dinamik ve dinamik olmayan davranış arasında geçiş yapmasına olanak sağlar.

Aşağıdaki örneklerde gösterildiği gibi, herhangi bir nesne dinamik türe örtük olarak dönüştürülebilir.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Buna karşılık, örtük bir dönüştürme `dynamic` türünde herhangi bir ifadeye dinamik olarak uygulanabilir.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Dinamik türdeki bağımsız değişkenlerle aşırı yükleme çözümlemesi

Bir yöntem çağrısındaki bir veya daha fazla bağımsız değişken `dynamic`, ya da yöntem çağrısının alıcısı `dynamic` türünde ise, aşırı yükleme çözümlemesi, derleme zamanı yerine çalışma zamanında gerçekleşir. Aşağıdaki örnekte, tek bir dize bağımsız değişkeni almak için yalnızca erişilebilir `exampleMethod2` yöntemi tanımlanırsa, bağımsız değişken olarak `d1` gönderme bir derleyici hatasına neden olmaz, ancak çalışma zamanı özel durumuna neden olur. @No__t_0 çalışma zamanı türü `int` olduğundan ve `exampleMethod2` bir dize gerektirdiğinden aşırı yükleme çözümlemesi çalışma zamanında başarısız olur.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma zamanı

Dinamik dil çalışma zamanı (DLR) .NET Framework 4 ' te yeni bir API 'dir. İçinde C#`dynamic` türünü destekleyen altyapıyı ve ayrıca IronPython ve IronRuby gibi dinamik programlama dillerinin uygulanmasını sağlar. DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM birlikte çalışma

C#4, Office Otomasyonu API 'leri gibi COM API 'lerle birlikte çalışma deneyimini geliştiren çeşitli özellikler içerir. Geliştirmeler arasında `dynamic` türünün ve [adlandırılmış ve isteğe bağlı bağımsız değişkenlerin](../classes-and-structs/named-and-optional-arguments.md)kullanımı vardır.

Birçok COM yöntemi, türleri `object` olarak tanımlayarak bağımsız değişken türlerinde ve dönüş türünde değişimler için izin verir. Bu, ' deki kesin olarak belirlenmiş değişkenlerle koordine etmek için değerlerin açık bir şekilde C#çevrim kümesini gerektiren bir [-Link (C# derleyici seçenekleri)](../../language-reference/compiler-options/link-compiler-option.md) seçeneğini kullanarak derlerseniz `dynamic` türünün kullanıma sunulması, com imzalarındaki `object` tekrarlamalarını `dynamic` türü gibi kabul etmenizi ve dolayısıyla çok sayıda atama yapılmasını önlemenize olanak sağlar. Örneğin, aşağıdaki deyimler Microsoft Office Excel elektronik tablosundaki bir hücreye `dynamic` türü ve `dynamic` türü olmadan nasıl erişirsiniz.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[dynamic](../../language-reference/keywords/dynamic.md)|@No__t_0 anahtar sözcüğünün kullanımını açıklar.|
|[Dinamik Dil Çalışma Zamanına Genel Bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Ortak dil çalışma zamanına (CLR) dinamik diller için bir hizmet kümesi ekleyen bir çalışma zamanı ortamı olan DLR 'ye genel bir bakış sağlar.|
|[İzlenecek yol: dinamik nesneler oluşturma ve kullanma](walkthrough-creating-and-using-dynamic-objects.md)|Özel dinamik nesne oluşturmaya ve bir `IronPython` kitaplığına erişen bir proje oluşturmaya yönelik adım adım yönergeler sağlar.|
|[Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim](../interop/how-to-access-office-onterop-objects.md)|Adlandırılmış ve isteğe bağlı bağımsız değişkenler, `dynamic` türü ve Office API nesnelerine erişimi kolaylaştıran diğer geliştirmeleri kullanan bir projenin nasıl oluşturulacağını gösterir.|
