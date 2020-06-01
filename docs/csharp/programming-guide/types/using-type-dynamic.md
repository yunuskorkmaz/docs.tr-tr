---
title: Tür dinamik-C# Programlama Kılavuzu kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 24d48605e560038d70f1818611f339a94ecc2bba
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241974"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Tür dinamik kullanma (C# Programlama Kılavuzu)

C# 4 yeni bir tür tanıtır `dynamic` . Tür statik bir türdür, ancak türünde bir nesne `dynamic` statik tür denetimini atlar. Çoğu durumda, bu, türü gibi çalışır `object` . Derleme zamanında, olarak yazılan bir öğe `dynamic` herhangi bir işlemi destekleyecek şekilde varsayılır. Bu nedenle, nesnenin değerini bir COM API 'sinden, IronPython gibi dinamik bir dilden, HTML Belge Nesne Modeli (DOM), yansımasından veya programdaki herhangi bir yerden alıp ulaşmamasından endişe etmeniz gerekmez. Ancak, kod geçerli değilse, hatalar çalışma zamanında yakalanmalıdır.

Örneğin, `exampleMethod1` aşağıdaki kodda bulunan örnek yönteminin yalnızca bir parametresi varsa, derleyici `ec.exampleMethod1(10, 4)` iki bağımsız değişken içerdiğinden, yöntemin ilk çağrısının geçerli olmadığını algılar. Çağrı, bir derleyici hatasına neden olur. Öğesinin türü olduğundan, yöntemi için ikinci çağrı `dynamic_ec.exampleMethod1(10, 4)` derleyici tarafından denetlenmez `dynamic_ec` `dynamic` . Bu nedenle, hiçbir derleyici hatası bildirilmemiştir. Ancak, hata süresiz olarak çıkış yapmaz. Çalışma zamanında yakalanır ve bir çalışma zamanı özel durumuna neden olur.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Bu örneklerde derleyicinin rolü, her bir deyimin, olarak yazılan nesne veya ifade için hangi şekilde önerdikleridir hakkındaki bilgileri birlikte paketlemenize olanak sağlar `dynamic` . Çalışma zamanında, depolanan bilgiler incelenir ve geçerli olmayan herhangi bir ifade çalışma zamanı özel durumuna neden olur.

Çoğu dinamik işlemin sonucu kendi kendisidir `dynamic` . Örneğin, fare işaretçisini aşağıdaki örnekte öğesinin kullanımı üzerine getirdiğinizde `testSum` , IntelliSense türü **(yerel değişken) dinamik testsum**' ı görüntüler.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Sonucun `dynamic` içermediği işlemler:

* ' Den `dynamic` başka bir türe dönüşümler.
* Türündeki bağımsız değişkenleri içeren Oluşturucu çağrıları `dynamic` .

Örneğin, `testInstance` aşağıdaki bildirimde türü `ExampleClass` değildir `dynamic` :

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Dönüştürme örnekleri aşağıdaki "Dönüşümler" bölümünde gösterilmiştir.

## <a name="conversions"></a>Dönüşümler

Dinamik nesneler ve diğer türler arasındaki dönüştürmeler kolaydır. Bu, geliştiricinin dinamik ve dinamik olmayan davranış arasında geçiş yapmasına olanak sağlar.

Aşağıdaki örneklerde gösterildiği gibi, herhangi bir nesne dinamik türe örtük olarak dönüştürülebilir.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Buna karşılık örtük bir dönüştürme, türünde herhangi bir ifadeye dinamik olarak uygulanabilir `dynamic` .

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Dinamik türdeki bağımsız değişkenlerle aşırı yükleme çözümlemesi

Bir yöntem çağrısında bir veya daha fazla bağımsız değişken türü varsa `dynamic` veya yöntem çağrısının alıcısı tür ise, yükleme çözümü derleme zamanı yerine çalışma zamanında gerçekleşir `dynamic` . Aşağıdaki örnekte, tek `exampleMethod2` bir dize bağımsız değişkeni almak için yalnızca erişilebilir Yöntem tanımlanmışsa, `d1` bağımsız değişken olarak gönderme bir derleyici hatasına neden olmaz, ancak çalışma zamanı özel durumuna neden olur. Çalışma zamanı türü `d1` olduğu `int` ve `exampleMethod2` bir dize gerektirdiğinden aşırı yükleme çözümlemesi çalışma zamanında başarısız olur.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma zamanı

Dinamik dil çalışma zamanı (DLR), .NET Framework 4 ' te tanıtılan bir API 'dir. `dynamic`C# ' deki türü destekleyen altyapıyı ve ayrıca IronPython ve IronRuby gibi dinamik programlama dillerinin uygulanmasını sağlar. DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM birlikte çalışma

C# 4, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışma deneyimini geliştiren çeşitli özellikler içerir. Geliştirmeler arasında `dynamic` , türünün ve [adlandırılmış ve isteğe bağlı bağımsız değişkenlerin](../classes-and-structs/named-and-optional-arguments.md)kullanımı vardır.

Birçok COM yöntemi, türleri olarak tanımlayarak bağımsız değişken türlerinde ve dönüş türünde değişimler için izin verir `object` . Bu, C# ' de kesin türü belirtilmiş değişkenlerle koordine etmek için değerlerin açık bir şekilde çevrim kümesini gerektiren bir [-Link (C# derleyici seçenekleri)](../../language-reference/compiler-options/link-compiler-option.md) seçeneğini kullanarak derlerseniz, `dynamic` türün tanıtımı `object` com imzalarındaki tekrarlamalarını, türü gibi kabul etmenizi `dynamic` ve dolayısıyla bu nedenle çok sayıda atamayı önlemeyi sağlar. Örneğin, aşağıdaki deyimler Microsoft Office Excel elektronik tablosundaki bir hücreye türü `dynamic` ve türü olmadan nasıl erişirsiniz `dynamic` .

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[dynamic](../../language-reference/builtin-types/reference-types.md)|`dynamic`Anahtar sözcüğünün kullanımını açıklar.|
|[Dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Ortak dil çalışma zamanına (CLR) dinamik diller için bir hizmet kümesi ekleyen bir çalışma zamanı ortamı olan DLR 'ye genel bir bakış sağlar.|
|[İzlenecek yol: dinamik nesneler oluşturma ve kullanma](walkthrough-creating-and-using-dynamic-objects.md)|Özel dinamik nesne oluşturmak ve bir kitaplığa erişen proje oluşturmak için adım adım yönergeler sağlar `IronPython` .|
|[Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](../interop/how-to-access-office-onterop-objects.md)|Adlandırılmış ve isteğe bağlı bağımsız değişkenleri, `dynamic` türü ve OFFICE API nesnelerine erişimi kolaylaştıran diğer geliştirmeleri kullanan bir projenin nasıl oluşturulacağını gösterir.|
