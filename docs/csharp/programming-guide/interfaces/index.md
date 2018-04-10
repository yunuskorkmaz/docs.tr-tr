---
title: Arabirimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: 45
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f14d4bf48d117558a4019a8f016e194af27a9ebf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)
Bir arabirim ilgili işlevlerin bir grup için tanımları içerir, bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) uygulayabilirsiniz.  
  
 Arabirimleri kullanarak bir sınıf içinde birden fazla kaynaktan davranış örneğin, dahil edebilirsiniz. Dil sınıfların birden çok devralma desteklemediğinden bu C# ' de önemli bir özelliktir. Buna ek olarak, bunlar aslında başka bir yapı veya sınıfı olamaz devraldığı yapılar, devralma benzetimini yapmak istiyorsanız, bir arabirim kullanmanız gerekir.  
  
 Kullanarak bir arabirim tanımlayın [arabirimi](../../../csharp/language-reference/keywords/interface.md) aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Herhangi bir sınıf veya uygulayan yapısı <xref:System.IEquatable%601> arabirimi için bir tanım içermelidir bir <xref:System.IEquatable%601.Equals%2A> arabirimi belirtir imza eşleşen yöntemi. Sonuç olarak, uygulayan bir sınıf sayabilirsiniz `IEquatable<T>` içerecek şekilde bir `Equals` ile sınıfının bir örneği belirleyebilir aynı sınıfın başka bir örneğe eşit olup olmadığını yöntemi.  
  
 Tanımını `IEquatable<T>` için uygulama sağlamaz `Equals`. Arabirimi yalnızca imza tanımlar. Bu şekilde, bir arabirim, C# tüm yöntemleri soyut bir Özet sınıfa benzer. Sınıfta veya yapı birden çok arabirimi uygulayabilirsiniz, ancak, bir sınıfın yalnızca tek bir sınıf, Özet veya devralabilirsiniz. Bu nedenle, arabirimleri kullanarak, bir sınıf içinde birden fazla kaynaktan davranışı içerebilir.  
  
 Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Arabirim yöntemleri, özellikleri, olayları, dizin oluşturucular veya bu dört üye türleri herhangi bir birleşimini içerebilir. Örnekler bağlantıları için bkz: [ilgili bölümler](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Arabirim sabitleri, alanları, işleçleri, örnek oluşturucuları, sonlandırıcılar veya türleri içeremez. Arabirim üyeleri otomatik olarak ortak ve hiçbir erişim değiştiricileri içeremez. Üyeler ayrıca olamaz [statik](../../../csharp/language-reference/keywords/static.md).  
  
 Uygulayan sınıfa karşılık gelen üyesi arabirim üyesini uygulamak için genel, statik olmayan ve aynı ad ve imza arabirimi üye olarak olması gerekir.  
  
 Sınıfta veya yapı bir arabirimini uygulayan, bir uygulama sınıfta veya yapı tüm arabirimi tanımlar üyeleri için sağlaması gerekir. Arabirimi, temel sınıf işlevselliğini devrettiği sınıfta veya yapı biçiminde devrettiği hiçbir işlevsellik sağlar. Ancak, bir taban sınıf bir arabirim uygularsa, temel sınıfından türetilmiş herhangi bir sınıf, uygulama devralır.  
  
 Aşağıdaki örnek, IEquatable uygulaması gösterir. < T\> arabirimi. Uygulayan sınıfa `Car`, uygulaması sağlamalısınız <xref:System.IEquatable%601.Equals%2A> yöntemi.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 Özellikler ve dizin oluşturucular bir sınıfta bir özellik veya bir arabiriminde tanımlanan dizin oluşturucu için ek erişimciler tanımlayabilirsiniz. Örneğin, bir arabirim sahip bir özelliği bildirme bir [almak](../../../csharp/language-reference/keywords/get.md) erişimcisi. Arabirimini uygulayan sınıf her ikisi de aynı özelliğiyle bildirebilir bir `get` ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimcisi. Ancak, özellik veya dizin oluşturucu açık uygulama kullanıyorsa, erişimciler eşleşmelidir. Açık uygulaması hakkında daha fazla bilgi için bkz: [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) ve [arabirimi özelliklerini](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 Arabirimleri diğer arabirimleri uygulayabilir. Bir sınıf bir arabirim devralır birden çok kez temel sınıfları veya diğer arabirimlerini arabirimleri aracılığıyla içerebilir. Sınıf sınıf tanımının bir parçası olarak arabirimi bildirirse ancak sınıfı bir arabirim uygulaması zaman ve yalnızca tek bir sağlayabilir (`class ClassName : InterfaceName`). Arabirimini uygulayan bir temel sınıf devraldığından arabirimi devralınmışsa arabirimi üyeleri uygulaması temel sınıf sağlar. Ancak, türetilmiş sınıf devralınan uygulama kullanmak yerine arabirim üyelerini yeniden uygulamalı.  
  
 Bir taban sınıf, sanal üyeler kullanarak arabirim üyelerini de uygulayabilirsiniz. Bu durumda, türetilmiş bir sınıf, sanal üyeleri geçersiz kılma tarafından arabirimi davranışı değiştirebilirsiniz. Sanal üyeler hakkında daha fazla bilgi için bkz: [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Arabirim Özetleri  
 Bir arabirim aşağıdaki özelliklere sahiptir:  
  
-   Özet temel sınıf gibi bir arabirimdir. Herhangi bir sınıf veya arabirimini uygulayan yapısı tüm üyeleri uygulamalıdır.  
  
-   Arabirim doğrudan örneği oluşturulamıyor. Üyeleri herhangi bir sınıf veya arabirimini uygulayan yapısı tarafından uygulanır.  
  
-   Arabirimleri olayları, dizin oluşturucular, yöntemleri ve özellikleri içerebilir.  
  
-   Hiçbir uygulama yöntemlerinin arabirimleri içerir.  
  
-   Sınıfta veya yapı birden çok arabirimi uygulayabilirsiniz. Bir sınıf bir taban sınıf ve ayrıca bir veya daha fazla arabirimin uygulayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Arabirime belirli bir sınıf üyesi oluşturma açıklanmaktadır.  
  
 [Nasıl yapılır: arabirim üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Arabirimin üyelerini açıkça uygulama konusunda bir örnek sağlar.  
  
 [Nasıl yapılır: iki arabirimin üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Devralma ile arabirimin üyelerini açıkça uygulama konusunda bir örnek sağlar.  
  
##  <a name="BKMK_RelatedSections"></a>İlgili bölümler  
  
-   [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Arabirimlerdeki dizin oluşturucular](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Olayları](../../../csharp/programming-guide/events/index.md)  
  
-   [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Özel Kitap Bölümü  
 [Arabirimleri](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) içinde [C# 3.0 öğrenme: C# 3.0 temelleri Yöneticisi](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
