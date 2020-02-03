---
title: Soyutlama Uygulamak için Temel Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: b22923338f8488b6f7684e565f62d9afc16e6aa0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741770"
---
# <a name="base-classes-for-implementing-abstractions"></a>Soyutlama Uygulamak için Temel Sınıflar
Kesinlikle konuşurken, bir sınıf başka bir sınıf bundan türetildiği zaman bir temel sınıf haline gelir. Ancak, bu bölümün amacına yönelik olarak, temel sınıf genellikle ortak bir soyutlama sağlamak için veya diğer sınıfların devralma sırasında bazı varsayılan uygulamaları yeniden kullanabilmesi için tasarlanmış bir sınıftır. Temel sınıflar genellikle, bir hiyerarşinin kökündeki bir soyutlama ve alt kısımdaki birkaç özel uygulama arasındaki devralma hiyerarşilerinin ortasında yer vardır.

 Soyutlamalar uygulamak için uygulama yardımcıları olarak görev yapar. Örneğin, çatı öğe koleksiyonları için çerçeve soyutlarından biri <xref:System.Collections.Generic.IList%601> arabirimidir. <xref:System.Collections.Generic.IList%601> uygulamak önemsiz değildir ve bu nedenle Framework, özel koleksiyonlar uygulamak için yardımcılar olarak işlev gösteren <xref:System.Collections.ObjectModel.Collection%601> ve <xref:System.Collections.ObjectModel.KeyedCollection%602>gibi çeşitli temel sınıflar sağlar.

 Temel sınıflar genellikle çok fazla uygulama içereceğinden, kendilerine soyut olarak sunulacak şekilde uygun değildir. Örneğin, `Collection<T>` temel sınıfı, genel olmayan `IList` arabirimini (genel olmayan koleksiyonlarla daha iyi tümleşecek şekilde) ve alanlarından birinde bellekte depolanan öğelerin bir koleksiyonu olduğunu bulmadan ilgili çok sayıda uygulama içerir.

 Daha önce anlatıldığı gibi temel sınıflar, soyutlamalar uygulaması gereken kullanıcılar için değerli yardım sağlayabilir, ancak aynı zamanda önemli bir yükümlülük olabilir. Bunlar yüzey alanı ekler ve devralma hiyerarşilerinin derinliğini artırır ve bu sayede Framework 'ü karmaşıklaştırır. Bu nedenle, temel sınıfların yalnızca Framework kullanıcılarına önemli bir değer sağladıklarında kullanılması gerekir. Yalnızca çerçevenin uygulayıcılarına değer sağladıklarında kaçınılması gerekir, bu durum bir temel sınıftan devralınması yerine bir iç uygulamaya yönelik temsilinin kesin olarak dikkate alınması gerekir.

 ✔️, herhangi bir soyut üye içermese de, temel sınıfların soyut olmasını düşünün. Bu, sınıfın yalnızca devralınacağı şekilde tasarlanan kullanıcılarla açıkça iletişim kurar.

 ✔️ temel sınıfları ana hat senaryo türlerinden ayrı bir ad alanına yerleştirmeyi düşünün. Tanım olarak, temel sınıflar gelişmiş genişletilebilirlik senaryolarına yöneliktir ve bu nedenle kullanıcıların çoğunluğu için ilginç değildir.

 sınıfın ortak API 'lerde kullanılması amaçlanıyorsa, temel sınıfların bir "temel" sonekiyle adlandırılmasının önüne ❌.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
