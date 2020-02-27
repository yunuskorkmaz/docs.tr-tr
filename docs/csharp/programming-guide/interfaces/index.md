---
title: Arabirimler- C# Programlama Kılavuzu
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 99cbaa458e86c644a46eb62823f1854b3684c6c4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627753"
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)

Bir arabirim, soyut olmayan bir [sınıfın](../../language-reference/keywords/class.md) veya [yapının](../../language-reference/builtin-types/struct.md) uygulanması gereken ilgili işlevler grubu için tanımlar içerir. Bir arabirim, bir uygulamaya sahip olması gereken `static` Yöntemler tanımlayabilir. Arabirim, tanımlanmış örnek üyelerinin tümü veya tümü için varsayılan bir uygulama sağlayabilir. Arabirim, alanlar, otomatik uygulanan özellikler ya da özellik benzeri olaylar gibi örnek verileri bildiremeyebilir.

Arabirimleri kullanarak, örneğin, bir sınıftaki birden çok kaynaktan davranış ekleyebilirsiniz. Dil, sınıfların birden çok C# devralınmasını desteklemediğinden bu özellik önemlidir. Bunlara ek olarak, başka bir struct veya sınıftan gerçekten devralmadıklarından yapılar için devralmayı taklit etmek istiyorsanız bir arabirim kullanmanız gerekir.

Aşağıdaki örnekte gösterildiği gibi [arabirim](../../language-reference/keywords/interface.md) anahtar sözcüğünü kullanarak bir arabirim tanımlarsınız.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Arabirimin adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Kural gereği, arabirim adları büyük `I`başlar.

<xref:System.IEquatable%601> arabirimini uygulayan herhangi bir sınıf veya yapı, arabirimin belirttiği imzayla eşleşen bir <xref:System.IEquatable%601.Equals%2A> yöntemi tanımı içermelidir. Sonuç olarak, sınıfının bir örneğinin aynı sınıfın başka bir örneğine eşit olup olmadığını belirleyebildiği bir `Equals` yöntemi içermesi için `IEquatable<T>` uygulayan bir sınıf üzerinde sayım yapabilirsiniz.

`IEquatable<T>` tanımı `Equals`için bir uygulama sağlamaz. Bir sınıf veya yapı birden çok arabirim uygulayabilir, ancak bir sınıf yalnızca tek bir sınıftan devralınabilir.

Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Arabirimler örnek yöntemler, özellikler, olaylar, Dizin oluşturucular veya bu dört üye türlerinin herhangi bir birleşimini içerebilir. Arabirimler statik oluşturucular, alanlar, sabitler veya işleçler içerebilir. Örneklere bağlantılar için [Ilgili bölümler](./index.md#BKMK_RelatedSections)bölümüne bakın. Arabirim, örnek alanları, örnek oluşturucular veya sonlandırıcılar içeremez. Arabirim üyeleri varsayılan olarak açıktır.

Bir arabirim üyesini uygulamak için, uygulama sınıfının karşılık gelen üyesi ortak, statik değil olmalıdır ve arabirim üyesiyle aynı ada ve imzaya sahip olmalıdır.

Bir sınıf veya yapı bir arabirim uygularsa, sınıf veya yapı birimi arabirimin bildirdiği, ancak için varsayılan bir uygulama sağlamayan Tüm üyeler için bir uygulama sağlamalıdır. Ancak, bir temel sınıf bir arabirim uygularsa, taban sınıftan türetilmiş herhangi bir sınıf bu uygulamayı devralır.

Aşağıdaki örnek, <xref:System.IEquatable%601> arabiriminin bir uygulamasını gösterir. Uygulama sınıfı `Car`, <xref:System.IEquatable%601.Equals%2A> yönteminin bir uygulamasını sağlamalıdır.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Bir sınıfın özellikleri ve Dizin oluşturucular, bir arabirimde tanımlı bir özellik veya Dizin Oluşturucu için ek erişimciler tanımlayabilir. Örneğin, bir arabirim bir [Get](../../language-reference/keywords/get.md) erişimcisine sahip bir özellik bildirebilir. Arabirimini uygulayan sınıf, hem `get` hem de [set](../../language-reference/keywords/set.md) erişimcisi ile aynı özelliği bildirebilir. Ancak, özellik veya Dizin Oluşturucu açık uygulama kullanıyorsa, erişimcilerinin eşleşmesi gerekir. Açık uygulama hakkında daha fazla bilgi için bkz. [Açık arabirim uygulama](explicit-interface-implementation.md) ve [arabirim özellikleri](../classes-and-structs/interface-properties.md).

Arabirimler, bir veya daha fazla arabirimden devralınabilir. Türetilmiş arabirim, üyeleri temel arabirimlerinden devralır. Türetilmiş arabirimi uygulayan bir sınıf, türetilmiş arabirimin temel arabirimlerinin tüm üyeleri dahil olmak üzere türetilmiş arabirimdeki tüm üyeleri uygulamalıdır. Bu sınıf örtük olarak türetilmiş arabirime veya temel arabirimlerinden dönüştürülebilir. Bir sınıf, devraldığı temel sınıflar veya diğer arabirimlerin devraldığı arabirimler aracılığıyla birden çok kez arabirim içerebilir. Ancak, sınıfı bir arabirimin uygulamasını yalnızca bir kez ve yalnızca sınıf sınıfın tanımının bir parçası olarak bildirir (`class ClassName : InterfaceName`). Arabirimi uygulayan bir temel sınıf devralmış olduğunuz için arabirim devralınmışsa, taban sınıf arabirimin üyelerinin uygulanmasını sağlar. Ancak, türetilen sınıf devralınan uygulamayı kullanmak yerine herhangi bir sanal arabirim üyesini yeniden uygulayabilir. Arabirimler bir yöntemin varsayılan uygulamasını bildiriyorsa, bu arabirimi uygulayan herhangi bir sınıf bu uygulamayı devralır. Arabirimlerde tanımlı uygulamalar sanal ve uygulama sınıfı bu uygulamayı geçersiz kılabilir.

Bir temel sınıf, sanal Üyeler kullanarak arabirim üyeleri de uygulayabilir. Bu durumda, türetilmiş bir sınıf sanal üyeleri geçersiz kılarak arabirim davranışını değiştirebilir. Sanal üyeler hakkında daha fazla bilgi için bkz. çok [biçimlilik](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Arabirimler Özeti

Bir arabirim aşağıdaki özelliklere sahiptir:

- Bir arabirim, genellikle yalnızca soyut üyelere sahip bir soyut temel sınıf gibidir. Arabirimi uygulayan herhangi bir sınıf veya yapının tüm üyelerini uygulaması gerekir. İsteğe bağlı olarak, bir arabirim, üyelerinin bazıları veya tümü için varsayılan uygulamaları tanımlayabilir.
- Arabirim doğrudan başlatılamaz. Üyeleri, arabirimini uygulayan herhangi bir sınıf veya yapı tarafından uygulanır.
- Bir sınıf veya yapı, birden çok arabirim uygulayabilir. Bir sınıf bir temel sınıfı devralınabilir ve ayrıca bir veya daha fazla arabirim uygulayabilir.

## <a name="BKMK_RelatedSections"></a>İlgili bölümler

- [Arabirim Özellikleri](../classes-and-structs/interface-properties.md)  
- [Arabirimlerdeki Dizin Oluşturucular](../indexers/indexers-in-interfaces.md)  
- [Arabirim olaylarını uygulama](../events/how-to-implement-interface-events.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)  
- [Devralma](../classes-and-structs/inheritance.md)  
- [Yöntemler](../classes-and-structs/methods.md)  
- [Çok biçimlilik](../classes-and-structs/polymorphism.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Özellikler](../classes-and-structs/properties.md)  
- [Olaylar](../events/index.md)  
- [Dizin Oluşturucular](../indexers/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Devralma](../classes-and-structs/inheritance.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
