---
title: Yapılar - C# Kılavuzu
description: Yapı türü ve bunları nasıl oluşturacağınız hakkında bilgi edinin
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 6fcd30907880be9159b3cc2e3ab10659ddec248b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706461"
---
# <a name="structs"></a>Yapılar
A *yapı* bir değer türüdür. Bir yapı oluşturulduğunda yapının atanmış olduğu değişken yapının gerçek verilerini tutar. Struct için yeni bir değişken atandığında kopyalanır. Bu nedenle yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyaya yapılan değişiklikler diğer kopyayı etkilemez.

Değer türü değişkenler doğrudan değerlerini, değişkenin bildirildiği hangi bağlamda satır içi bellek tahsis edildiği anlamına gelir içerir. Ayrı yığın atama veya değer türü değişkenler çöp toplama taşması yoktur.  
  
Değer türlerinin iki kategorisi vardır: [yapı](./language-reference/keywords/struct.md) ve [enum](./language-reference/keywords/enum.md).  
  
Yerleşik sayısal türler yapı birimleridir ve özellikleri ve yöntemleri erişebileceğiniz sahiptirler:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ancak bildirmek ve bunların basit toplama olmayan türlermiş gibi bunlara değer atayamazsınız:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Değer türleri *korumalı*, yani, örneğin, bir türden türetilemez <xref:System.Int32>, ve bir yapı yalnızca kaynağından devralabileceğinden bir kullanıcı tanımlı sınıf veya yapıdan devralacak bir yapı tanımlayamazsınız <xref:System.ValueType> . Ancak, bir yapının bir veya daha fazla arabirim uygulayabilir. Bir yapı türünü bir arabirim türüne çevirebilirsiniz; Bu neden olan bir *kutulama* yönetilen yığında struct bir başvuru türü nesnesi içine sarmak için işlemi. Kutulama işlemleri, bir değer türü alan bir yönteme geçirdiğinizde meydana bir <xref:System.Object> giriş parametresi olarak. Daha fazla bilgi için [kutulama ve kutudan çıkarma](./programming-guide/types/boxing-and-unboxing.md ).  
  
Kullandığınız [yapı](./language-reference/keywords/struct.md) kendi özel değer türlerinizi oluşturmak için anahtar sözcüğü. Genellikle, bir yapının bir kapsayıcı gibi küçük bir ilişkili değişken kümesi için aşağıdaki örnekte gösterildiği gibi kullanılır:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework içindeki değer türleri hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../standard/common-type-system.md).  
    
Yapılar sınıfları daha sınırlı olmasına karşın yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:  
  
- Alanlar olarak bildirilmedikleri sürece bir yapının bildirimi içinde başlatılamaz `const` veya `static`.  
  
- Bir yapı, parametresiz bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.  
  
- Yapılar, atamaya bağlı kopyalanır. Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez. Bu, sözlük < string, myStruct > gibi değer türlerinin koleksiyonları ile çalışırken unutmamak önemlidir.  
  
- Yapılar değer türüdür ve sınıflar, başvuru türleridir.  
  
- Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.  
  
- Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.  
  
- Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.  
  
- Bir yapı, arabirim uygulayabilir.

## <a name="literal-values"></a>Değişmez değerler  
C# dilinde değişmez değerler derleyiciden bir tür alır. Sayı sonuna bir harf ekleyerek sayısal değişmez değerin nasıl yazılacağını belirtebilirsiniz. Örneğin, 4.56 değerinin kaydırma olarak ele alınması gerektiğini belirtmek için bir "f" veya "F" sayı sonra Ekle: `4.56f`. Hiçbir harf eklenirse, derleyici çıkarımlar `double` değişmez değer türü. Hangi belirtilebilen türler harf sonekleri daha fazla bilgi için her bir türe ilişkin başvuru sayfalarına bakın [değer türleri](./language-reference/keywords/value-types.md).  
  
Değişmez değerler olduğu ve tüm türler nihai olarak türetmek için gelen <xref:System.Object>, yazabilir ve aşağıdaki gibi kodu derleyin:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Son iki örnekler C# 7.0 sunulan dil özellikleri gösterir. İlk olarak bir alt çizgi karakteri kullanmanıza olanak tanır bir *basamak ayıracı* sayısal değişmez değerleri içinde. Bunları okunabilirliği artırmak için basamakların arasında istediğiniz yere koyabilirsiniz. Değerin üzerinde etkiye sahiptirler.

İkinci gösterir *ikili sabit dizeler*, onaltılık gösterimini kullanmak yerine doğrudan bit desenleri belirtmek sağlar.

## <a name="nullable-types"></a>Boş değer atanabilir tipler  
Sıradan değer türleri değerine sahip [null](./language-reference/keywords/null.md). Ancak, boş değer atanabilen değer türleri ekleyerek oluşturabileceğiniz bir **?** sonra türü. Örneğin, **int?** olduğu bir **int** değeri de olabilir bir tür [null](./language-reference/keywords/null.md). CTS içinde boş değer atanabilir türler genel yapı türünün örnekleridir <xref:System.Nullable%601>. Boş değer atanabilir türler için ve veritabanlarına sayı değerleri null olabilir veri geçirirken özellikle kullanışlıdır. Daha fazla bilgi için [boş değer atanabilir türler (C# programlama Kılavuzu)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](classes.md)
- [Temel Türler](basic-types.md)
