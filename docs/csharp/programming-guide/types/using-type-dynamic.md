---
title: Kullanarak dinamik - yazın C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 7c4e2aac613397fbd44f4594f96ddebfb75d0c3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678841"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Tür dinamiği (C# programlama Kılavuzu) kullanma

[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] Yeni bir tür tanıtır `dynamic`. Türü bir nesne türü ancak statik bir tür olduğunda `dynamic` statik tür denetimi atlar. Çoğu durumda, bu tür gibi işlevleri `object`. Derleme zamanında olarak belirlenmiş bir öğe `dynamic` destekleyen herhangi bir işlem olarak kabul edilecektir. Bu nedenle olup nesne değeri COM API'sinden, IronPython gibi dinamik bir dili, HTML belge nesne modeli (DOM) öğesinden, yansıma veya programda başka bir yere öğesinden alır merak gerekmez. Ancak, kod geçerli değilse hataları çalışma zamanında yakalanır.

Örneğin, örnek yöntemi `exampleMethod1` aşağıdaki kodu yalnızca bir parametresi vardır, derleyici tanıyan yöntemine yapılan ilk çağrı `ec.exampleMethod1(10, 4)`, iki bağımsız değişkeni içerdiğinden geçerli değil. Çağrı, bir derleyici hatasına neden olur. Yöntem için yapılan ikinci çağrı `dynamic_ec.exampleMethod1(10, 4)`, derleyici tarafından çünkü işaretlenmediği türünü `dynamic_ec` olduğu `dynamic`. Bu nedenle, derleyici hata bildirilir. Ancak, hata bildirimi süresiz olarak kaçırmaz. Bu, çalışma zamanında yakalanabilmesini ve çalışma zamanı özel durumuna neden olur.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Bu örneklerde derleyicinin hangi her deyim nesnesi veya olarak yazdığınız ifade önerdiği hakkında bilgi birlikte paketlemek için rolüdür `dynamic`. Çalışma zamanında depolanan bilgilerin incelenir ve geçerli değil herhangi bir deyimle bir çalışma zamanı özel durumuna neden olur.

Çoğu dinamik işlem kendisini sonucudur `dynamic`. Örneğin, kullanımı fare işaretçisini getirdiğinizde `testSum` aşağıdaki örnekte, IntelliSense türünü görüntüler **(yerel değişken) dinamik testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

İşlemler, sonuç değil `dynamic` içerir:

* Dönüşümlerse `dynamic` başka bir türe.
* Tür bağımsız değişkenleri ekleyin ve oluşturucu çağrıları `dynamic`.

Örneğin, türü `testInstance` içinde aşağıdaki bildirim `ExampleClass`değil `dynamic`:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Aşağıdaki bölümde, "Dönüştürme" dönüştürme örnekler gösterilmektedir

## <a name="conversions"></a>Dönüşümler

Dinamik nesneler ve diğer türleri arasında dönüştürmeler kolaydır. Bu, dinamik ve dinamik olmayan davranış arasında geçiş yapmak Geliştirici sağlar.

Herhangi bir nesne için dinamik tür aşağıdaki örneklerde gösterildiği gibi örtük olarak dönüştürülebilir.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Buna karşılık, örtük bir dönüştürme dinamik olarak türünde herhangi bir ifade için uygulanabilir `dynamic`.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Aşırı yükleme çözümlemesi dinamik türdeki bağımsız değişken

Aşırı yükleme çözünürlüğü oluşursa yerine derleme zamanında çalışma zamanında bir veya daha fazla yöntem çağrısında bağımsız değişken türü `dynamic`, ya da yöntem çağrısının alıcı türü ise `dynamic`. Aşağıdaki örnekte, yalnızca erişilebilir `exampleMethod2` yöntemi bir dize bağımsız değişken alan için tanımlanmış gönderme `d1` bağımsız değişkeni bir derleyici hatasına neden olmaz, ancak bir çalışma zamanı özel durumuna neden olmaz. Çalışma zamanı türü olmadığından aşırı yükleme çözümlemesi başarısız çalışma zamanında `d1` olduğu `int`, ve `exampleMethod2` bir dize gerektirir.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma zamanı

Dinamik dil çalışma zamanı (DLR) yeni bir API'dir [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Destekleyen altyapı sağlar `dynamic` C# ve ayrıca dinamik programlama dillerinin IronPython ve Ironruby gibi uygulama türü. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM birlikte çalışma

[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] Office Otomasyonu API'leri gibi COM API'leri ile birlikte deneyimini geliştiren çeşitli özellikler içerir. Kullanımını geliştirmeleridir arasında `dynamic` türü ve [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md).

Birçok COM yöntemi için bağımsız değişken türleri varyasyonu izin ve dönüş türü türleri olarak tanımlayarak `object`. Bu, C# türü kesin belirlenmiş değişkenleri ile koordine etmek için değerleri açık atama olmaması. Kullanarak derleme yaparsanız [/Link (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) seçeneği, giriş `dynamic` türü etkinleştirir, oluşumunu değerlendirilecek `object` COM imzalarında türünü değilmiş gibi `dynamic`ve dolayısıyla atama çoğunu önlemek için. Örneğin, aşağıdaki ifadeleri ile Microsoft Office Excel elektronik tablosundaki bir hücre erişmenizi nasıl Karşıtlık `dynamic` türü ve olmadan `dynamic` türü.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[dynamic](../../language-reference/keywords/dynamic.md)|Kullanımını açıklar `dynamic` anahtar sözcüğü.|
|[Dinamik Dil Çalışma Zamanına Genel Bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Dinamik Dil Hizmetleri bir dizi ortak dil çalışma zamanı (CLR) ekleyen bir çalışma zamanı ortamıdır DLR genel bir bakış sağlar.|
|[İzlenecek yol: Dinamik nesneler oluşturma ve kullanma](walkthrough-creating-and-using-dynamic-objects.md)|Özel bir dinamik Nesne oluşturma ve erişen bir proje oluşturmak için adım adım yönergeler sağlar. bir `IronPython` kitaplığı.|
|[Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../interop/how-to-access-office-onterop-objects.md)|Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanan bir proje oluşturma işlemini gösterir `dynamic` türü ve Office API'nin nesnelere erişimi kolaylaştıran diğer geliştirmeler.|