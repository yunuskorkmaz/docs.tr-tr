---
title: 'Arabirimleri - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
  - 'interfaces [C#]'
  - 'C# language, interfaces'
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)

Bir arabirim ilgili işlevler bir grup için tanımları içeren, bir [sınıfı](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/keywords/struct.md) uygulayabilirsiniz.
  
Arabirimleri kullanarak, bir sınıfta birden çok kaynaktan davranışı gibi dahil edebilirsiniz. Dil sınıflarının birden çok devralma desteklemediğinden, C# ' de önemli bir özelliktir. Ayrıca, yapılar için devralmayı benzetimi yapmak istiyorsanız, aslında başka bir yapı veya sınıf devralınamaz çünkü bir arabirimini kullanmanız gerekir.  
  
Bir arabirim kullanarak tanımladığınız [arabirimi](../../language-reference/keywords/interface.md) anahtar sözcüğü. Aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md). Kural gereği, arabirimi adlarını büyük harf ile başlayan `I`.

Herhangi bir sınıfın veya yapının uyguladığı <xref:System.IEquatable%601> arabirimi için bir tanım içermelidir bir <xref:System.IEquatable%601.Equals%2A> arabirimi belirtir imzayla eşleşen yöntemi. Sonuç olarak uygulayan bir sınıf güvenebilirsiniz `IEquatable<T>` içerecek şekilde bir `Equals` yöntemi ile bir sınıf örneği belirleyebilir aynı sınıfın başka bir örneğe eşit olup olmadığını.  
  
Tanımı `IEquatable<T>` için bir uygulama sağlamaz `Equals`. Arabirimi yalnızca imzası tanımlar. Bu şekilde, C# dilinde bir arabirim yöntemleri soyut bir soyut sınıf benzer. Ancak, bir sınıfın veya yapının birden fazla arabirim uygulayabilir, ancak bir sınıf veya yalnızca tek bir sınıf, soyut devralabilir.
  
Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Arabirim yöntemleri, özellikleri, olayları, dizin oluşturucular veya bu dört üye türleri herhangi bir birleşimini içerebilir. Örnekler için bağlantılar için bkz. [ilgili bölümler](../interfaces/index.md#BKMK_RelatedSections). Bir arabirim, sabitleri, alanları, işleçleri, örnek oluşturucuları, bir sonlandırıcı veya türleri içeremez. Arabirim üyelerini otomatik olarak herkese açık ve hiçbir erişim değiştiricileri dahil edemezsiniz. Üyeler de olamaz [statik](../../language-reference/keywords/static.md).  
  
Uygulayan sınıfa karşılık gelen üyesi bir arabirim üyesi uygulamak için genel, statik olmayan ve aynı ada ve imzaya arabirim üyesi olması gerekir.  
  
Bir sınıf veya yapı, arabirim uygular, bir uygulama sınıfın veya yapının tüm arabirimi tanımlar üyeleri için sağlamanız gerekir. Arabirimi, temel sınıf işlevselliğini devralabilir biçiminde bir sınıf veya yapı devralabilir hiçbir işlevsellik sağlar. Ancak, bir temel sınıf, arabirim uygularsa, bu uygulamayı temel sınıftan türetilmiş herhangi bir sınıf devralır.  
  
Aşağıdaki örnek bir uygulamasını gösterir <xref:System.IEquatable%601> arabirimi. Uygulayan sınıfa `Car`, bir uygulamasını sağlamalıdır <xref:System.IEquatable%601.Equals%2A> yöntemi.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Özellikler ve dizin oluşturucular bir sınıfın özellik veya arabirim içinde tanımlanmış bir dizin oluşturucu için ek erişimcileri tanımlayabilirsiniz. Örneğin, bir arabirimi olan bir özelliği bildirme bir [alma](../../language-reference/keywords/get.md) erişimcisi. Arabirimi uygulayan bir sınıf her ikisi de aynı özellik bildirebilirsiniz bir `get` ve [ayarlamak](../../language-reference/keywords/set.md) erişimcisi. Ancak, özellik veya dizin oluşturucu açık uygulama kullanıyorsa, erişimcileri eşleşmesi gerekir. Açık uygulama hakkında daha fazla bilgi için bkz: [açık arabirim uygulaması](explicit-interface-implementation.md) ve [arabirimi özellikleri](../classes-and-structs/interface-properties.md).  

Arabirim, diğer bir arabirimden devralabilir. Bir sınıf, arabirimin devraldığı birden çok kez temel sınıflar veya diğer arabirimleri devralan arabirimleri aracılığıyla içerebilir. Sınıf arabirimi sınıf tanımının bir parçası bildirir, ancak sınıfın bir arabirim uygulaması zaman ve yalnızca tek bir sağlayabilirsiniz (`class ClassName : InterfaceName`). Arabirimini uygulayan bir temel sınıf devraldığından arabirimi devralınmışsa temel sınıfın arabirim üyelerinin uygulamasını sağlar. Ancak, türetilmiş sınıf, devralınmış uygulaması yerine tüm sanal arabirim üyeleri yeniden uygulayın.  
  
Bir taban sınıfı sanal üye kullanarak arabirim üyelerini de uygulayabilirsiniz. Bu durumda, türetilmiş bir sınıf sanal üyelerini geçersiz kılarak arabirimi davranışı değiştirebilirsiniz. Sanal üyeler hakkında daha fazla bilgi için bkz: [çok biçimlilik](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Arabirim özetleri

Bir arabirim, aşağıdaki özelliklere sahiptir:  

- Bir arabirim yalnızca soyut üye bir soyut temel sınıf gibidir. Herhangi bir sınıfı veya arabirimi uygulayan yapı tüm üyeleri uygulamalıdır.
- Bir arabirimi doğrudan başlatılamaz. Üyeleri herhangi bir sınıfı veya arabirimi uygulayan yapı tarafından uygulanır.
- Arabirimleri, olaylar, dizin oluşturucular, yöntemler ve özellikler içerebilir.
- Arabirim yöntemleri uygulaması içerir.
- Bir sınıf veya yapı birden fazla arabirim uygulayabilir. Bir sınıf, bir taban sınıfı ve ayrıca bir veya daha fazla arabirimi uygulayan.

## <a name="in-this-section"></a>Bu bölümde

[Belirtik Arabirim Kullanma](explicit-interface-implementation.md)  
 Arabirime belirli bir sınıf üyesinin oluşturma açıklanır.  
  
 [Nasıl yapılır: Arabirim üyelerini açıkça uygulama](how-to-explicitly-implement-interface-members.md)  
 Arabirimin üyelerini açıkça uygulama ilişkin bir örnek sağlar.  
  
 [Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Devralma ile arabirimin üyelerini açıkça uygulama ilişkin bir örnek sağlar.  
  
## <a name="BKMK_RelatedSections"></a> İlgili bölümler

- [Arabirim Özellikleri](../classes-and-structs/interface-properties.md)  
- [Arabirimlerdeki Dizin Oluşturucular](../indexers/indexers-in-interfaces.md)  
- [Nasıl yapılır:  Arabirim olaylarını uygulama](../events/how-to-implement-interface-events.md)  
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)  
- [Devralma](../classes-and-structs/inheritance.md)  
- [Yöntemler](../classes-and-structs/methods.md)  
- [Çok biçimlilik](../classes-and-structs/polymorphism.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Özellikler](../classes-and-structs/properties.md)  
- [Olaylar](../events/index.md)  
- [Dizin Oluşturucular](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Özel Kitap bölümü

[Arabirimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) içinde [öğrenme C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Devralma](../classes-and-structs/inheritance.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
