---
title: Çok biçimlilik - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 489fdf87f973de6137587fc2280ef0fa72ab78ba
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286461"
---
# <a name="polymorphism-c-programming-guide"></a>Çok Biçimlilik (C# Programlama Kılavuzu)
Çok biçimlilik genellikle kapsülleme ve devralma sonra nesne yönelimli programlama, üçüncü sütun olarak adlandırılır. Çok biçimlilik "çok biçimli" anlamına gelen Yunanca sözcüktür ve iki ayrı görünüşlere sahiptir:  
  
-   Çalışma zamanında, türetilmiş bir sınıfın nesnelerini yöntem parametreleri ve koleksiyonları veya diziler gibi yerlerde bir taban sınıfın nesneleri olarak değerlendirilecek. Bu durumda, bildirilen nesnenin türü artık çalışma zamanı türünü aynıdır.  
  
-   Taban sınıfları tanımlama ve uygulama [sanal](../../../csharp/language-reference/keywords/virtual.md) *yöntemleri*, ve türetilen sınıflar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) bunları kendi tanım ve uygulamayı sağladıkları anlamına gelir. CLR istemci kodu yöntemi çağırdığında, çalışma zamanında, nesnenin çalışma zamanı türünü arar ve o sanal yöntemini geçersiz kılma çağırır. Bu nedenle, kaynak kodunuzda bir temel sınıf üzerinde bir yöntemi çağırabilir ve yürütülecek yöntemin türetilmiş sınıf sürümü neden.  
  
 Sanal yöntemleri ile ilgili nesnelerin gruplarını Tekdüzen bir şekilde çalışmanıza olanak sağlar. Örneğin, kullanıcının bir çizim yüzeyinde şekiller çeşitli oluşturmasını sağlayan bir çizim uygulama olduğunu varsayalım. Derleme zamanında hangi türde şekiller kullanıcı oluşturacak bilmezsiniz. Ancak, çeşitli türleri oluşturulan şekillerinin izlemek uygulamada var ve yanıt olarak kullanıcı fare işlemlerini güncelleştirmeniz gerekir. Çok biçimlilik, iki temel adımlar bu sorunu çözmek için kullanabilirsiniz:  
  
1.  Her özel şekil sınıfı ortak bir taban sınıftan türetilen bir sınıf hiyerarşisi oluşturun.  
  
2.  Sanal bir yöntem, tek bir temel sınıf yöntemini çağrı yoluyla herhangi bir türetilmiş sınıf üzerinde uygun yöntemini çağırmak için kullanın.  
  
 İlk olarak, adlı temel bir sınıf oluşturun `Shape`ve gibi türetilmiş sınıflar `Rectangle`, `Circle`, ve `Triangle`. Vermek `Shape` sınıfı olarak adlandırılan sanal bir yöntemi `Draw`, geçersiz kılma belirli çizmek için her bir türetilmiş sınıf içinde şekil, bir sınıfı temsil eder. Oluşturma bir `List<Shape>` nesnesi ve bir daire, üçgen ve dikdörtgen ekleyin. Çizim yüzeyini güncelleştirmek için bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) listesi ve arama yinelemek için döngü `Draw` yöntemi her `Shape` listesinde nesne. Listedeki her nesne bir türü sahip olsa da `Shape`, çağrılacak çalışma zamanı tür (her türetilmiş bir sınıf yöntemi geçersiz kılınan sürümü).  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 Kullanıcı tanımlı türler dahil olmak üzere tüm türleri devralınacak C# içinde her tür çok biçimli olduğundan <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Çok biçimlilik genel bakış  
  
### <a name="virtual-members"></a>Sanal üyeler  
 Türetilmiş bir sınıf bir taban sınıftan devraldığında tüm yöntemler, alanlar, özellikler ve olaylar temel sınıfın kazanır. Türetilmiş sınıf Tasarımcısı seçebilirsiniz verilip verilmeyeceğini  
  
-   sanal taban sınıfı üyeleri geçersiz kıl  
  
-   en yakın temel sınıf yöntemini geçersiz kılma olmadan devral  
  
-   Yeni sanal olmayan taban sınıf uygulamaları Gizle bu üyeler uygulamasını tanımlayın  
  
 Yalnızca temel sınıf üyesi olarak bildirilirse, türetilmiş bir sınıf bir temel sınıf üyesi geçersiz kılabilirsiniz [sanal](../../../csharp/language-reference/keywords/virtual.md) veya [soyut](../../../csharp/language-reference/keywords/abstract.md). Türetilen üye kullanmalısınız [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) açıkça yöntemi sanal bir çağrıda katılmak düşünüldüğünü göstermek için anahtar sözcüğü. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Alanlar sanal olamaz; yalnızca yöntemler, özellikler, olaylar ve dizin oluşturucular sanal olabilir. Türetilmiş bir sınıf sanal bir üye değiştirdiğinde, bu üye temel sınıfın bir örneği bu sınıfın bir örneğini bile erişiliyor çağrılır. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Sanal yöntemleri ve özellikleri türetilmiş sınıflar temel sınıf uygulamasına bir yöntem kullanmak zorunda kalmadan bir temel sınıf genişletmek etkinleştirin. Daha fazla bilgi için [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Arabirimdeki bir yöntem veya uygulaması türetilen sınıflar için sola yöntemleri kümesini tanımlamak için başka bir yol sağlar. Daha fazla bilgi için [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Yeni üyeler ile taban sınıfı üyeleri gizleme  
 Türetilmiş üyelik bir temel sınıfta bir üye ile aynı ada sahip olmasını istediğiniz ancak bunu sanal bir çağrıda katılmak istemiyorsanız, kullanabileceğiniz [yeni](../../../csharp/language-reference/keywords/new.md) anahtar sözcüğü. `new` Anahtar sözcüğü bir sınıf üyesinin değiştirilmekte olan dönüş türünden önce yerleştirin. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Gizli bir temel sınıf üyeleri, türetilmiş sınıf temel sınıfın bir örneğine örneğini atayarak istemci kodundan hala erişilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Sanal üyeler geçersiz kılmasını önlemek türetilen sınıflar  
 Sanal üyeler, kaç sınıflar olarak bildirilen sınıfı sanal üye arasında kaldırıldığı bildirilen bağımsız olarak sanal kalır. C sınıf B'den türeyen bir sınıf sanal bir üye bildirir ve B sınıf A'dan türer, C sınıfı sanal üye devralır ve geçersiz kılmak, bağımsız olarak, bu üye için bir geçersiz kılma bildirilen B sınıf olup seçeneğine sahiptir. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Türetilmiş bir sınıf için bir geçersiz kılma olarak bildirerek sanal devralma durdurabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md). Bu yerleştirme gerektirir `sealed` anahtar sözcüğünün önüne `override` sınıf üyesi bildiriminde anahtar sözcüğü. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 Önceki örnekte, yöntem `DoWork` artık sanal C'den türetilmiş sınıfına değil C örnekleri B türü veya tür a korumalı yöntemler cast olsa bile değiştirilebilir için türetilmiş sınıfları tarafından kullanarak yine de sanal `new` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 Bu durumda, `DoWork` D, türünde bir değişken kullanarak D adlı yeni `DoWork` çağrılır. C, B ve A türünde bir değişken D, bir çağrı örneğini erişmek için kullanılıp kullanılmadığını `DoWork` sanal devralma, bu çağrıları uygulanmasına yönelik yönlendirme kurallarını takip `DoWork` c sınıfı hakkında  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Sanal temel sınıf üyelerinin türetilmiş sınıflardan erişme  
 Sahip veya bir yöntem veya özellik geçersiz kılınan türetilmiş bir sınıf yöntem veya özellik temel anahtar sözcüğü kullanılarak taban sınıfta erişmeye devam edebilirsiniz. Aşağıdaki kod, bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Daha fazla bilgi için [temel](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Sanal üyeler kullanmanız önerilir `base` kendi uygulamasında, bu üyenin taban sınıf uygulamasını çağırmak için. Türetilmiş sınıfa özel davranış uygulayan hakkında yoğunlaşabilirsiniz türetilmiş sınıf sağlayan ortaya temel sınıf davranışını sağlar. Temel sınıf uygulamasına çağrılmaz, türetilmiş sınıf davranışlarını temel sınıfın davranışı ile uyumlu hale getirmek için en fazla olur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Nasıl yapılır: ToString yöntemini geçersiz kılma](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
- [Türler](../../../csharp/programming-guide/types/index.md)
