---
title: Soyutlama Uygulamak için Temel Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 6af63373b7cbb571265f14ac36028953525fcc7f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280575"
---
# <a name="base-classes-for-implementing-abstractions"></a>Soyutlama Uygulamak için Temel Sınıflar
Kesinlikle konuşurken, bir sınıf başka bir sınıf bundan türetildiği zaman bir temel sınıf haline gelir. Ancak, bu bölümün amacına yönelik olarak, temel sınıf genellikle ortak bir soyutlama sağlamak için veya diğer sınıfların devralma sırasında bazı varsayılan uygulamaları yeniden kullanabilmesi için tasarlanmış bir sınıftır. Temel sınıflar genellikle, bir hiyerarşinin kökündeki bir soyutlama ve alt kısımdaki birkaç özel uygulama arasındaki devralma hiyerarşilerinin ortasında yer vardır.

 Soyutlamalar uygulamak için uygulama yardımcıları olarak görev yapar. Örneğin, çerçevenin sıralı koleksiyonları için çerçeve soyutlarından biri <xref:System.Collections.Generic.IList%601> arayüzüdür. Uygulama <xref:System.Collections.Generic.IList%601> önemsiz değildir ve bu nedenle Framework, ve gibi çeşitli temel sınıflar sağlar <xref:System.Collections.ObjectModel.Collection%601> ve <xref:System.Collections.ObjectModel.KeyedCollection%602> Özel Koleksiyonlar uygulamak için yardımcılar olarak işlev yapar.

 Temel sınıflar genellikle çok fazla uygulama içereceğinden, kendilerine soyut olarak sunulacak şekilde uygun değildir. Örneğin, `Collection<T>` temel sınıf, genel olmayan `IList` arabirimi (genel olmayan koleksiyonlarla daha iyi tümleşecek şekilde) ve kendi alanlarından birinde bellekte depolanan öğelerin bir koleksiyonu olduğu olgusuna ilişkin büyük bir uygulama içerir.

 Daha önce anlatıldığı gibi temel sınıflar, soyutlamalar uygulaması gereken kullanıcılar için değerli yardım sağlayabilir, ancak aynı zamanda önemli bir yükümlülük olabilir. Bunlar yüzey alanı ekler ve devralma hiyerarşilerinin derinliğini artırır ve bu sayede Framework 'ü karmaşıklaştırır. Bu nedenle, temel sınıfların yalnızca Framework kullanıcılarına önemli bir değer sağladıklarında kullanılması gerekir. Yalnızca çerçevenin uygulayıcılarına değer sağladıklarında kaçınılması gerekir, bu durum bir temel sınıftan devralınması yerine bir iç uygulamaya yönelik temsilinin kesin olarak dikkate alınması gerekir.

 ✔️, herhangi bir soyut üye içermese de, temel sınıfların soyut olmasını düşünün. Bu, sınıfın yalnızca devralınacağı şekilde tasarlanan kullanıcılarla açıkça iletişim kurar.

 ✔️ temel sınıfları ana hat senaryo türlerinden ayrı bir ad alanına yerleştirmeyi düşünün. Tanım olarak, temel sınıflar gelişmiş genişletilebilirlik senaryolarına yöneliktir ve bu nedenle kullanıcıların çoğunluğu için ilginç değildir.

 ❌Sınıfın ortak API 'lerde kullanılması amaçlanıyorsa, temel sınıfların bir "temel" sonekiyle adlandırılmasını ÖNLEYIN.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
