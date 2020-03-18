---
title: Arayüzler - C# Programlama Kılavuzu
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: f4ee269f41e79562c113a7627816f797b083095e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79157084"
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)

Arabirim, soyut olmayan bir [sınıfın](../../language-reference/keywords/class.md) veya [bir yapının](../../language-reference/builtin-types/struct.md) uygulaması gereken ilgili işlevler grubu için tanımlar içerir. Arabirim, `static` uygulanması gereken yöntemleri tanımlayabilir. Arabirim, bildirilen örnek üyelerinden herhangi biri veya tümü için varsayılan bir uygulama sağlayabilir. Arabirim, alanlar, otomatik olarak uygulanan özellikler veya özellik benzeri olaylar gibi örnek verileri bildirmeyebilir.

Arabirimleri kullanarak, örneğin, bir sınıftaki birden çok kaynaktan gelen davranışları ekleyebilirsiniz. Bu özellik C#'da önemlidir, çünkü dil sınıfların birden çok kalıtımını desteklemez. Ayrıca, başka bir yapı veya sınıftan devralamayacağından, yapı için kalıtım benzetimi yapmak istiyorsanız bir arabirim kullanmanız gerekir.

Aşağıdaki örnekte görüldüğü gibi [arabirim](../../language-reference/keywords/interface.md) anahtar sözcüklerini kullanarak bir arabirim tanımlarsınız.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Arabirimin adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Sözleşmeye göre, arabirim `I`adları büyük harfle başlar.

<xref:System.IEquatable%601> Arabirimi uygulayan herhangi bir sınıf veya yapı, arabirimin belirttiği imzayla eşleşen bir <xref:System.IEquatable%601.Equals%2A> yöntem için bir tanım içermelidir. Sonuç olarak, sınıfın bir örneğinin aynı `IEquatable<T>` sınıfın `Equals` başka bir örneğine eşit olup olmadığını belirleyebileceği bir yöntem içerecek şekilde uygulayan bir sınıfa güvenebilirsiniz.

Tanımı için `IEquatable<T>` `Equals`bir uygulama sağlamaz. Bir sınıf veya yapı birden çok arabirim uygulayabilir, ancak bir sınıf yalnızca tek bir sınıftan devralınabilir.

Soyut sınıflar hakkında daha fazla bilgi için [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri'ne](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)bakın.

Arabirimler örnek yöntemleri, özellikleri, olaylar, dizinleyiciler veya bu dört üye türlerin herhangi bir birleşimi içerebilir. Arabirimler statik yapıcılar, alanlar, sabitler veya işleçler içerebilir. Örneklere bağlantılar için [İlgili Bölümler'e](./index.md#BKMK_RelatedSections)bakın. Arabirim örnek alanları, örnek oluşturucular veya sonlandırıcılar içeremez. Arabirim üyeleri varsayılan olarak herkese açıktır.

Bir arabirim üyesi uygulamak için, uygulama sınıfının ilgili üyesinin ortak, statik olmayan ve arabirim üyesiyle aynı ad ve imzaya sahip olması gerekir.

Bir sınıf veya yapı bir arabirim uyguladığında, sınıf veya yapı, arabirimin bildirdiği ancak varsayılan bir uygulama sağlamadığı tüm üyeler için bir uygulama sağlamalıdır. Ancak, bir taban sınıf bir arabirim uygularsa, taban sınıftan türetilen herhangi bir sınıf bu uygulamayı devralır.

Aşağıdaki örnek, <xref:System.IEquatable%601> arabirimin bir uygulamasını gösterir. Uygulama sınıfı, `Car` <xref:System.IEquatable%601.Equals%2A> yöntemin bir uygulama sağlamalıdır.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Bir sınıfın özellikleri ve dizinleyicileri, arabirimde tanımlanan bir özellik veya dizinleyici için ek erişimciler tanımlayabilir. Örneğin, arabirim, [erişime sahip](../../language-reference/keywords/get.md) bir özelliği bildirebilir. Arabirimi uygulayan sınıf, hem a `get` hem de [set](../../language-reference/keywords/set.md) erişimcisi ile aynı özelliği bildirebilir. Ancak, özellik veya dizinleyici açık uygulama kullanıyorsa, erişimedenler eşleşmelidir. Açık uygulama hakkında daha fazla bilgi için açık [arabirim uygulaması](explicit-interface-implementation.md) ve [Arabirim Özellikleri'ne](../classes-and-structs/interface-properties.md)bakın.

Arabirimler bir veya daha fazla arabirimden devralınabilir. Türetilen arabirim, üyeleri temel arabirimlerinden devralır. Türetilen arabirimi uygulayan bir sınıfın, türemiş arabirimin temel arabirimlerinin tüm üyeleri de dahil olmak üzere türemiş arabirimdeki tüm üyeleri uygulaması gerekir. Bu sınıf örtülü olarak türemiş arabirime veya temel arabirimlerinden herhangi biri olarak dönüştürülebilir. Bir sınıf, devraldığı temel sınıflar veya diğer arabirimler tarafından devralınan arabirimler aracılığıyla birden çok kez bir arabirim içerebilir. Ancak, sınıf yalnızca bir kez ve yalnızca sınıf sınıfının tanımının bir parçası olarak arabirimi`class ClassName : InterfaceName`bildirirse bir arabirim uygulaması sağlayabilir ( . Arabirimi uygulayan bir taban sınıf devraldığınız için arabirim devralılırsa, taban sınıf arabirimin inüyelerini sağlar. Ancak, türetilen sınıf, devralınan uygulamayı kullanmak yerine herhangi bir sanal arabirim üyesini yeniden uygulayabilir. Arabirimler bir yöntemin varsayılan uygulamasını bildirdiğinde, bu arabirimi uygulayan herhangi bir sınıf bu uygulamayı devralır. Arabirimlerde tanımlanan uygulamalar sanaldır ve uygulama sınıfı bu uygulamayı geçersiz kılabilir.

Taban sınıf, sanal üyeleri kullanarak arabirim üyelerini de uygulayabilir. Bu durumda, türetilmiş bir sınıf sanal üyeleri geçersiz kılarak arabirim davranışını değiştirebilir. Sanal üyeler hakkında daha fazla bilgi için [Polymorphism'e](../classes-and-structs/polymorphism.md)bakın.

## <a name="interfaces-summary"></a>Arayüzler özeti

Arabirim aşağıdaki özelliklere sahiptir:

- Arabirim genellikle yalnızca soyut üyeleri olan soyut bir taban sınıfı gibidir. Arabirimi uygulayan herhangi bir sınıf veya yapı tüm üyelerini uygulamalıdır. İsteğe bağlı olarak, bir arabirim bazı veya tüm üyeleri için varsayılan uygulamaları tanımlayabilir.
- Bir arayüz doğrudan anlık olamaz. Üyeleri, arabirimi uygulayan herhangi bir sınıf veya yapı tarafından uygulanır.
- Bir sınıf veya yapı birden çok arabirim uygulayabilir. Bir sınıf bir taban sınıf devralabilir ve aynı zamanda bir veya daha fazla arabirim uygulayabilirsiniz.

## <a name="BKMK_RelatedSections"></a>İlgili Bölümler

- [Arayüz Özellikleri](../classes-and-structs/interface-properties.md)  
- [Arabirimlerdeki Dizin Oluşturucular](../indexers/indexers-in-interfaces.md)  
- [Arabirim olaylarını uygulama](../events/how-to-implement-interface-events.md)
- [Sınıflar ve Structs](../classes-and-structs/index.md)  
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
