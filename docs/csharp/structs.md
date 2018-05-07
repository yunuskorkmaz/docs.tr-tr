---
title: Yapılar - C# Kılavuzu
description: Yapı türü ve bunları oluşturma hakkında bilgi edinin
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 9fe4e0278ecf46f762a93aa489030c0a9e5563b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="structs"></a>Yapılar
A *yapısı* değer türü değil. Yapı oluşturulurken yapı atandığı değişkeni yapının gerçek veri tutar. Yapı için yeni bir değişken atandığında, kopyalanır. Bu nedenle yeni değişken ve özgün değişkeni iki ayrı bir kopyasını aynı verileri içerir. Bir kopya için yapılan değişiklikler diğer kopya etkilemez.

Değer türü değişkenleri bellek satır değişkeni bildirilmiş herhangi bir bağlamı içinde ayrılır başka bir deyişle, bunların değerleri doğrudan içerir. Ayrı yığın ayırma veya değer türü değişkenleri için atık toplama yükünü yoktur.  
  
Değer türleri iki kategorisi vardır: [yapısı](./language-reference/keywords/struct.md) ve [enum](./language-reference/keywords/enum.md).  
  
Yerleşik sayısal yapıları türleridir ve sahip oldukları özellikleri ve yöntemleri erişebilirsiniz:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ancak bildirme ve basit olmayan türler değilmiş gibi değerler atayabilirsiniz:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Değer türleri *korumalı*, yani, örneğin, bir türünden türetilemez <xref:System.Int32>, ve yapı yalnızca devralınan çünkü herhangi bir kullanıcı tanımlı sınıf veya yapı devralmak için yapı tanımlayamazsınız <xref:System.ValueType> . Ancak, yapı bir veya daha fazla arabirimleri uygulayabilir. Bir arabirim türü bir yapı türüne çevirebilirsiniz; Bu neden olan bir *kutulama* yapısı içinde bir başvuru türü nesnesi yönetilen yığında kaydırma işlemi. Kutulama işlemleri gerçekleşmesi gereken bir yönteme bir değer türü geçirdiğinizde bir <xref:System.Object> giriş parametresi olarak. Daha fazla bilgi için bkz: [kutulama ve kutudan çıkarma](./programming-guide/types/boxing-and-unboxing.md ).  
  
Kullandığınız [yapısı](./language-reference/keywords/struct.md) kendi özel değer türleri oluşturmak için anahtar sözcüğü. Genellikle, yapı kapsayıcı olarak bir dizi ilgili değişkenler için aşağıdaki örnekte gösterildiği gibi kullanılır:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework'teki değer türleri hakkında daha fazla bilgi için bkz: [ortak tür sistemi](../standard/common-type-system.md).  
    
Yapılar sınıfları'den daha kısıtlı olsa yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:  
  
-   Yapı bildirimi içinde olarak bildirilir sürece alanlar başlatılamaz `const` veya `static`.  
  
-   Yapı, varsayılan bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.  
  
-   Yapılar atamada kopyalanır. Yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını kendilerine herhangi bir değişiklik özgün kopya verileri değiştirmez. Bu sözlük < string, myStruct > gibi değer türlerini koleksiyonlarıyla çalışırken unutmamak önemlidir.  
  
-   Yapılar değer türleri ve sınıfları başvuru türleri.  
  
-   Sınıfları kullanmadan yapılar oluşturulabilir bir `new` işleci.  
  
-   Yapılar parametrelere sahip oluşturucular bildirebilirsiniz.  
  
-   Yapı başka bir yapı veya sınıfından devralan ve bir sınıfın temel olamaz. Tüm yapıları doğrudan devralınmalıdır <xref:System.ValueType>, devralan <xref:System.Object>.  
  
-   Yapı arabirimleri uygulayabilir.

## <a name="literal-values"></a>Değişmez değerler  
C# ' ta değişmez değerler derleyiciden bir türü alır. Sayı sonuna bir harf ekleyerek tamsayısal bir hazır değer nasıl yazılmalıdır belirtebilirsiniz. Örneğin, 4.56 değeri float ele alınması gerektiğini belirtmek için bir "f" veya "F" sayıdan sonra sonuna: `4.56f`. Derleyici hiçbir harf eklenirse Infer `double` sabit türü. İçindeki tek tek türler için başvuru sayfaları hakkında türleri belirtilebilir harf öneklerle daha fazla bilgi için bkz: [değer türleri](./language-reference/keywords/value-types.md).  
  
Değişmez değerler yazılan ve tüm türleri sonuçta türetilen olduğundan gelen <xref:System.Object>, yazma ve aşağıdaki gibi kod derleme:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Son iki örnekler C# 7. 0'sunulan dil özellikleri gösterir. İlk olarak bir alt çizgi karakteri kullanmanıza olanak sağlayan bir *basamak ayırıcı* sayısal değişmez değerleri içinde. Okunabilirliğini artırmak için basamakların arasında istediğiniz yere bunları koyabilirsiniz. Bunlar değer üzerinde hiçbir etkisi yoktur.

İkinci gösterir *ikili değişmez değerleri*, onaltılık gösterim kullanılarak yerine doğrudan bit desenlerini belirtmek sağlar.

## <a name="nullable-types"></a>Boş değer atanabilir tipler  
Sıradan değer türleri değerine sahip olamaz [null](./language-reference/keywords/null.md). Ancak, boş değer atanabilen değer türleri affixing tarafından oluşturabileceğiniz bir **?** sonra türü. Örneğin, **int?** olan bir **int** değerini de alabilir türü [null](./language-reference/keywords/null.md). CTS boş değer atanabilir türler genel yapı türünün örnekleridir <xref:System.Nullable%601>. Boş değer atanabilir türler için ve sayısal değerleri null olabilir veritabanlarından veri geçirilirken özellikle yararlıdır. Daha fazla bilgi için bkz: [boş değer atanabilir türler (C# programlama Kılavuzu)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Ayrıca bkz.
[Sınıflar](classes.md)

[Temel Türler](basic-types.md)
