---
title: "Çok Biçimlilik (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 601c8cf626c846ca6c5d6bc2338e271e6b93544a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="polymorphism-c-programming-guide"></a>Çok Biçimlilik (C# Programlama Kılavuzu)
Çok biçimlilik genellikle kapsülleme ve devralma sonra nesne odaklı programlama üçüncü sütun olarak adlandırılır. Çok biçimlilik "çok şekillendirilmiş" anlamına gelir Yunanca bir sözcüktür ve iki ayrı görünüşlere sahiptir:  
  
-   Çalışma zamanında, türetilmiş bir sınıfın nesnelerini yerlerde yöntem parametreleri ve koleksiyonları veya dizi gibi temel bir sınıfın nesnelerini olarak kabul. Bu durumda, nesnenin türü artık çalışma zamanı türü için aynıdır.  
  
-   Temel sınıflar tanımlamak ve uygulama [sanal](../../../csharp/language-reference/keywords/virtual.md) *yöntemleri*, ve türetilen sınıflar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) bunları kendi tanımı ve uygulama sağladıkları anlamına gelir. Çalışma zamanında, istemci kodu yöntemini çağırır CLR nesnesinin çalışma zamanı türü arar ve bu geçersiz kılma sanal yöntemi çağırır. Bu nedenle kaynak kodunuzu bir temel sınıf üzerinde bir yöntemini çağırın ve yürütülecek yöntemi türetilmiş sınıf sürümünü neden.  
  
 Sanal yöntemler tek bir yolla ilgili nesneleri gruplarıyla çalışma olanak sağlar. Örneğin, çeşitli şekiller çizme yüzeyinde oluşturmak bir kullanıcının sağlayan bir çizim uygulaması olduğunu varsayalım. Derleme zamanında hangi türde şekiller kullanıcı oluşturacak bilmezsiniz. Ancak, tüm çeşitli türlerde oluşturulan şekiller izlemek uygulamada var ve kullanıcı fare eylemlerine güncelleştirmek vardır. Çok biçimlilik iki temel adımlar bu sorunu çözmek için kullanabilirsiniz:  
  
1.  Her belirli shape sınıfı ortak bir taban sınıftan türeyen bir sınıf hiyerarşisi oluşturun.  
  
2.  Temel sınıf yöntemi için tek bir çağrı aracılığıyla herhangi bir türetilmiş sınıf üzerinde uygun yöntemini çağırmak için sanal bir yöntem kullanın.  
  
 İlk olarak, adlı bir temel sınıf oluşturmak `Shape`ve türetilmiş sınıflar gibi `Rectangle`, `Circle`, ve `Triangle`. Vermek `Shape` adlı sanal bir yöntem sınıf `Draw`, ve geçersiz kılma belirli çizmek için her türetilmiş bir sınıf içinde şekil, sınıfı temsil eder. Oluşturma bir `List<Shape>` nesne ve bir daire, üçgen ve dikdörtgen ekleyin. Çizim yüzeyini güncelleştirmek için kullanın bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) listesi ve çağrı yinelemek için döngü `Draw` yöntemi her `Shape` listesinde nesnesi. Her nesne listesinde bildirilen türüne sahip olsa bile `Shape`, çağrılacak çalışma zamanı tür (her türetilmiş bir sınıf yöntemi geçersiz kılınan sürümü).  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 Kullanıcı tanımlı türler dahil olmak üzere tüm türleri devralınmalıdır C# ' ta her tür çok biçimli olduğundan <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Çok biçimlilik genel bakış  
  
### <a name="virtual-members"></a>Sanal üyeler  
 Türetilmiş bir sınıf bir taban sınıfından devralıyor, tüm yöntemleri, alanları, özellikleri ve olayları temel sınıfın kazanır. Türetilmiş sınıf Tasarımcısı seçebilirsiniz kullanılıp kullanılmayacağını  
  
-   sanal taban sınıfı üyeleri geçersiz kıl  
  
-   en yakın temel sınıf yöntemi geçersiz kılma olmadan devral  
  
-   Yeni sanal olmayan taban sınıf uygulamaları Gizle bu üyeler uyarlamasını tanımlayın  
  
 Yalnızca bir temel sınıf üyesi olarak bildirilirse türetilmiş bir sınıf bir taban sınıf üyesi kılabilirsiniz [sanal](../../../csharp/language-reference/keywords/virtual.md) veya [soyut](../../../csharp/language-reference/keywords/abstract.md). Türetilen üye kullanmalısınız [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) yöntemi içinde sanal çağırma katılmak için tasarlanmıştır açıkça belirtmek için anahtar sözcüğü. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Alanları sanal olamaz; yalnızca yöntemler, özellikler, olaylar ve dizin oluşturucular sanal olabilir. Türetilmiş bir sınıf sanal üyesi değiştirdiğinde bu sınıfının bir örneği temel sınıfının bir örneği erişiliyor bile, o üye adı verilir. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Sanal yöntemler ve Özellikler yöntemi temel sınıf uygulamasını kullanmaya gerek kalmadan bir taban sınıf genişletmek türetilen sınıflar sağlar. Daha fazla bilgi için bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Bir arabirim bir yöntemi veya, uygulama için türetilen sınıflar sol yöntemleri kümesini tanımlamak için başka bir yol sağlar. Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Taban sınıfı üyeleri yeni üyeleriyle gizleme  
 Bir taban sınıf içinde bir üye olarak aynı ada sahip türetilmiş üyelik istiyor ancak içinde sanal çağırma katılmasına olanak istemediğiniz, kullanabileceğiniz [yeni](../../../csharp/language-reference/keywords/new.md) anahtar sözcüğü. `new` Anahtar sözcüğü değiştirilmekte olan bir sınıf üyesi dönüş türü önce yerleştirin. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Gizli taban sınıfı üyeleri, istemci kodu temel sınıfın bir örneğine türetilmiş sınıf örneği atama tarafından hala erişilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Sanal üyeler geçersiz kılmasını önlemek türetilen sınıflar  
 Sanal üyeler süresiz olarak, kaç tane sınıfları sanal üyesi olarak bildirilen sınıf arasında bildirilmiş bağımsız olarak sanal kalır. C sınıfı B'den türeyen sınıf A sanal üyesi bildirir ve B sınıf A'dan türer, C sınıfı sanal üyesi devralır ve onu geçersiz kılmanıza, bağımsız olarak, bu üye için bir geçersiz kılma bildirilen B sınıf olup seçeneğine sahiptir. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Türetilmiş bir sınıf bir geçersiz kılma olarak bildirerek sanal devralma durdurabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md). Bu koyma gerektirir `sealed` önce anahtar sözcüğü `override` sınıf üyesi bildirim anahtar sözcük. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 Önceki örnekte, yöntem `DoWork` artık C'den türetilmiş herhangi bir sınıf sanal değil C örneklerini türü B veya türü A. korumalı yöntemleri cast olsa bile değiştirilebilir için türetilen sınıflar tarafından kullanarak hala sanal `new` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 Bu durumda, `DoWork` D, türünde bir değişken kullanarak D adlı yeni `DoWork` olarak adlandırılır. C, B ve A türünde bir değişken D, çağrı örneğini erişmek için kullanılıp kullanılmadığını `DoWork` sanal devralma, bu çağrıları uygulanmasına yönelik yönlendirme kurallarını izleyeceği `DoWork` sınıfındaki c  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Türetilmiş sınıflar temel sınıf sanal üyelere erişme  
 Sahip veya bir yöntemi veya özelliği geçersiz kılınmış türetilmiş sınıf yöntemi veya özelliği temel anahtar sözcüğünü kullanarak temel sınıf üzerinde erişmeye devam edebilirsiniz. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Daha fazla bilgi için bkz: [temel](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Sanal üyeler kullanmanız önerilir `base` kendi uygulamasında bu üyede temel sınıf uygulamasını çağırmak için. Türetilmiş bir sınıf üzerinde odaklanmasına olanak sağlayan ortaya temel sınıf davranışı izin vererek davranışı türetilmiş sınıf için belirli uygulama. Taban sınıfı uygulama çağrılmaz, türetilmiş bir sınıf davranışlarını temel sınıfı davranışını uyumlu hale getirmek için en fazla olur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Nasıl yapılır: ToString yöntemini geçersiz kılma](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)
