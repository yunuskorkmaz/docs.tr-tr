---
title: Tür dinamiği kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 67eb39fd6f2077d2adf1d38d001e801b815d687d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-type-dynamic-c-programming-guide"></a>Tür dinamiği kullanma (C# Programlama Kılavuzu)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] Yeni bir türü sunar `dynamic`. Türündeki bir nesne, ancak statik bir türü türüdür `dynamic` statik tür denetlemesi atlar. Çoğu durumda, türüne sahip gibi çalıştığından `object`. Derleme zamanında olarak yazılan bir öğe `dynamic` herhangi bir işlemi desteklemek için kabul edilir. Bu nedenle, olup nesne değeri COM API'sinden, dinamik bir dilden IronPython gibi HTML belge nesne modeli (DOM) gelen, yansıma veya programa başka bir yere alır endişelenmeniz gerekmez. Bununla birlikte, kod geçerli değilse, hataları zamanında yakalanır.  
  
 Örneğin, örnek yöntemi `exampleMethod1` aşağıdaki kodda yalnızca bir parametre içeriyor, derleyicisi tanır ilk çağrıda yöntemi `ec.exampleMethod1(10, 4)`, iki bağımsız değişken içerdiğinden geçerli değil. Çağrı derleyici hatasına neden olur. Yöntemi için ikinci çağrı `dynamic_ec.exampleMethod1(10, 4)`, çünkü derleyici tarafından işaretli türünü `dynamic_ec` olan `dynamic`. Bu nedenle, hiçbir derleyici hatası bildirilir. Ancak, hata bildirimi süresiz olarak kaçış değil. Çalışma zamanında yakalanan ve bir çalışma zamanı özel duruma neden olur.  
  
 [!code-csharp[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-csharp[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 Bu örneklerde derleyici rol birlikte ne her deyimi nesneye veya olarak yazılan ifade yapmak önerdiği hakkında bilgi paketlemektir `dynamic`. Çalışma zamanında depolanan bilgilerin incelenir ve bir çalışma zamanı özel durumu geçerli değil herhangi bir deyimle neden olur.  
  
 Çoğu dinamik işlemleri kendisini sonucudur `dynamic`. Örneğin kullanımını fare işaretçisini, `testSum` aşağıdaki örnekte, IntelliSense türünü görüntüler **(yerel değişken) dinamik testSum**.  
  
 [!code-csharp[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 İçinde sonuç değil işlemleri `dynamic` gelen dönüşümleri dahil `dynamic` başka bir türü ve bağımsız değişken türü dahil Oluşturucu çağrıları `dynamic`. Örneğin, türü `testInstance` aşağıdaki bildiriminde olan `ExampleClass`değil `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 Aşağıdaki bölümde, "Dönüşümler." dönüştürme örnekler gösterilmektedir  
  
## <a name="conversions"></a>Dönüşümler  
 Dinamik nesneler ve diğer türleri arasında dönüştürmeler kolaydır. Bu, dinamik ve dinamik olmayan davranışını arasında geçiş yapmak Geliştirici sağlar.  
  
 Herhangi bir nesne için dinamik tür dolaylı olarak, aşağıdaki örneklerde gösterildiği gibi dönüştürülebilir.  
  
 [!code-csharp[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 Buna karşılık, örtük bir dönüştürme dinamik olarak türü herhangi bir ifade için uygulanabilir `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Aşırı yükleme çözümü bağımsız değişken türü dinamik ile  
 Aşırı yükleme çözünürlüğü oluşursa çalışma zamanında yerine derleme zamanında bir veya daha fazla yöntem çağrısı değişkenlerinde türüne sahip `dynamic`, veya yöntem çağrısı alıcı türü ise `dynamic`. Aşağıdaki örnekte, yalnızca erişilebilir `exampleMethod2` yöntemi, bir dize bağımsız değişkeni yapılacak tanımlanır gönderme `d1` bağımsız değişkeni bir derleyici hatası neden olmaz ancak bir çalışma zamanı özel durumuna neden olarak. Aşırı yükleme çözünürlüğü başarısız çalışma zamanında çalışma zamanı türü olduğundan `d1` olan `int`, ve `exampleMethod2` bir dizesi gerektirir.  
  
 [!code-csharp[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Dinamik dil çalışma zamanı  
 Dinamik dil çalışma zamanı (DLR) yeni bir API'dir [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Destekleyen altyapısı sağlar `dynamic` türünü C# ve ayrıca IronPython ve IronRuby gibi dinamik programlama dilleri uygulamasıdır. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
## <a name="com-interop"></a>COM Birlikte Çalışma  
 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] Office Automation API'leri gibi COM API'leri ile birlikte deneyimini geliştirmek çeşitli özellikler içerir. Geliştirmeler arasında kullanımını edilir `dynamic` türü ve [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
 Birçok COM yöntemleri değişim bağımsız değişken türleri için izin verme ve dönüş türü türleri olarak tanımlayarak `object`. Bu, C# kesin türü belirtilmiş değişkenleriyle koordine etmek için değerlerin açık atama olmaması. Kullanarak derleme yaparsanız [/Link (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) seçeneği, giriş `dynamic` türü etkinleştirir oluşumları davranmanız `object` COM imzaları içinde türü değilmiş gibi `dynamic`ve böylece atama çoğunu önlemek için. Örneğin, aşağıdaki deyimleri ile Microsoft Office Excel elektronik tablodaki bir hücreyi nasıl erişim Karşıtlık `dynamic` türü ve olmadan `dynamic` türü.  
  
 [!code-csharp[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-csharp[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|Kullanımını açıklar `dynamic` anahtar sözcüğü.|  
|[Dinamik Dil Çalışma Zamanına Genel Bakış](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Ortak dil çalışma zamanı (CLR) dinamik diller için hizmetleri kümesi ekler bir çalışma zamanı ortamı DLR genel bir bakış sağlar.|  
|[İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|Özel bir dinamik Nesne oluşturma ve erişen bir proje oluşturmak için adım adım yönergeler sağlar bir `IronPython` kitaplığı.|  
|[Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|Adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanan bir proje oluşturmak nasıl gösteren `dynamic` türü ve Office API nesnelerine erişimi basitleştirmek diğer geliştirmeler.|
