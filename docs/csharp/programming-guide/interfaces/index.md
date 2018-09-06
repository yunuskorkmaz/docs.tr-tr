---
title: Arabirimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: fdbb220cd856fd7309d54c41a39f91a9316fe434
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736574"
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)
Bir arabirim ilgili işlevler bir grup için tanımları içeren, bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) uygulayabilirsiniz.  
  
 Arabirimleri kullanarak, bir sınıfta birden çok kaynaktan davranışı gibi dahil edebilirsiniz. Dil sınıflarının birden çok devralma desteklemediğinden, C# ' de önemli bir özelliktir. Ayrıca, yapılar için devralmayı benzetimi yapmak istiyorsanız, aslında başka bir yapı veya sınıf devralınamaz çünkü bir arabirimini kullanmanız gerekir.  
  
 Bir arabirim kullanarak tanımladığınız [arabirimi](../../../csharp/language-reference/keywords/interface.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Herhangi bir sınıfın veya yapının uyguladığı <xref:System.IEquatable%601> arabirimi için bir tanım içermelidir bir <xref:System.IEquatable%601.Equals%2A> arabirimi belirtir imzayla eşleşen yöntemi. Sonuç olarak uygulayan bir sınıf güvenebilirsiniz `IEquatable<T>` içerecek şekilde bir `Equals` yöntemi ile bir sınıf örneği belirleyebilir aynı sınıfın başka bir örneğe eşit olup olmadığını.  
  
 Tanımı `IEquatable<T>` için bir uygulama sağlamaz `Equals`. Arabirimi yalnızca imzası tanımlar. Bu şekilde, C# dilinde bir arabirim yöntemleri soyut bir soyut sınıf benzer. Ancak, bir sınıfın veya yapının birden fazla arabirim uygulayabilir, ancak bir sınıf veya yalnızca tek bir sınıf, soyut devralabilir. Bu nedenle, arabirimleri kullanarak, bir sınıfta birden çok kaynaktan davranışı içerebilir.  
  
 Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Arabirim yöntemleri, özellikleri, olayları, dizin oluşturucular veya bu dört üye türleri herhangi bir birleşimini içerebilir. Örnekler için bağlantılar için bkz. [ilgili bölümler](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Bir arabirim, sabitleri, alanları, işleçleri, örnek oluşturucuları, bir sonlandırıcı veya türleri içeremez. Arabirim üyelerini otomatik olarak herkese açık ve hiçbir erişim değiştiricileri dahil edemezsiniz. Üyeler de olamaz [statik](../../../csharp/language-reference/keywords/static.md).  
  
 Uygulayan sınıfa karşılık gelen üyesi bir arabirim üyesi uygulamak için genel, statik olmayan ve aynı ada ve imzaya arabirim üyesi olması gerekir.  
  
 Bir sınıf veya yapı, arabirim uygular, bir uygulama sınıfın veya yapının tüm arabirimi tanımlar üyeleri için sağlamanız gerekir. Arabirimi, temel sınıf işlevselliğini devralabilir biçiminde bir sınıf veya yapı devralabilir hiçbir işlevsellik sağlar. Ancak, bir temel sınıf, arabirim uygularsa, bu uygulamayı temel sınıftan türetilmiş herhangi bir sınıf devralır.  
  
 Aşağıdaki örnek, IEquatable uygulaması gösterir. < T\> arabirimi. Uygulayan sınıfa `Car`, bir uygulamasını sağlamalıdır <xref:System.IEquatable%601.Equals%2A> yöntemi.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 Özellikler ve dizin oluşturucular bir sınıfın özellik veya arabirim içinde tanımlanmış bir dizin oluşturucu için ek erişimcileri tanımlayabilirsiniz. Örneğin, bir arabirimi olan bir özelliği bildirme bir [alma](../../../csharp/language-reference/keywords/get.md) erişimcisi. Arabirimi uygulayan bir sınıf her ikisi de aynı özellik bildirebilirsiniz bir `get` ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimcisi. Ancak, özellik veya dizin oluşturucu açık uygulama kullanıyorsa, erişimcileri eşleşmesi gerekir. Açık uygulama hakkında daha fazla bilgi için bkz: [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) ve [arabirimi özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 Arabirim diğer arabirimleri uygulayabilir. Bir sınıf, arabirimin devraldığı birden çok kez temel sınıflar veya diğer arabirimleri uygulayan arabirimler üzerinden içerebilir. Sınıf arabirimi sınıf tanımının bir parçası bildirir, ancak sınıfın bir arabirim uygulaması zaman ve yalnızca tek bir sağlayabilirsiniz (`class ClassName : InterfaceName`). Arabirimini uygulayan bir temel sınıf devraldığından arabirimi devralınmışsa temel sınıfın arabirim üyelerinin uygulamasını sağlar. Ancak, türetilmiş sınıf, devralınmış uygulaması kullanmak yerine arabirim üyeleri yeniden uygulayın.  
  
 Bir taban sınıfı sanal üye kullanarak arabirim üyelerini de uygulayabilirsiniz. Bu durumda, türetilmiş bir sınıf sanal üyelerini geçersiz kılarak arabirimi davranışı değiştirebilirsiniz. Sanal üyeler hakkında daha fazla bilgi için bkz: [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Arabirim Özetleri  
 Bir arabirim, aşağıdaki özelliklere sahiptir:  
  
-   Bir soyut temel sınıf gibi bir arabirimdir. Herhangi bir sınıfı veya arabirimi uygulayan yapı tüm üyeleri uygulamalıdır.  
  
-   Bir arabirimi doğrudan başlatılamaz. Üyeleri herhangi bir sınıfı veya arabirimi uygulayan yapı tarafından uygulanır.  
  
-   Arabirimleri, olaylar, dizin oluşturucular, yöntemler ve özellikler içerebilir.  
  
-   Arabirim yöntemleri uygulaması içerir.  
  
-   Bir sınıf veya yapı birden fazla arabirim uygulayabilir. Bir sınıf, bir taban sınıfı ve ayrıca bir veya daha fazla arabirimi uygulayan.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Belirtik Arabirim Kullanma](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Arabirime belirli bir sınıf üyesinin oluşturma açıklanır.  
  
 [Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Arabirimin üyelerini açıkça uygulama ilişkin bir örnek sağlar.  
  
 [Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Devralma ile arabirimin üyelerini açıkça uygulama ilişkin bir örnek sağlar.  
  
##  <a name="BKMK_RelatedSections"></a> İlgili bölümler  
  
-   [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Arabirimlerdeki Dizin Oluşturucular](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Olaylar](../../../csharp/programming-guide/events/index.md)  
  
-   [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Özel Kitap Bölümü  
 [Arabirimleri](https://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) içinde [öğrenme: C# 3.0: Master the Fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
