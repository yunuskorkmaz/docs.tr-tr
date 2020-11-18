---
title: Ortak Tür Sistemi ve Ortak Dil Belirtimi
description: Ortak tür sistemi (CTS) ve ortak dil belirtiminin (CLS) .NET için birden çok dili desteklemesini olanaklı hale getirme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: e60205450e2f156407deb7be6b9c497d090b6f7b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822886"
---
# <a name="common-type-system--common-language-specification"></a>Ortak Tür Sistemi ve Ortak Dil Belirtimi

.NET dünyasında ücretsiz olarak kullanılan iki terim de, .NET uygulamasının nasıl çalıştığını anlamak ve nasıl çalıştığını anlamak için önemli bir şeydir.

## <a name="common-type-system"></a>Ortak Tür Sistemi

Baştan başlamak için bir .NET uygulamasının _dilden_ bağımsız olduğunu unutmayın. Bu, bir programcı 'nin kodunu Il 'ye derlenebilecek herhangi bir dilde yazabilmesi anlamına gelmez. Ayrıca, bir .NET uygulamasında kullanılabilecek diğer dillerde yazılmış kodla etkileşime girebilmeleri gereken anlamına gelir.

Bunu saydam yapmak için, desteklenen tüm türleri tanımlamanın ortak bir yolu olması gerekir. Bu, yaygın olarak kullanılan tür sisteminin (CTS) yapmakta olduğu şeydir. Birkaç şey yapmak için yapılmıştır:

* Diller arası yürütme için bir çerçeve oluşturun.
* .NET uygulamasında çeşitli dillerin uygulanmasını desteklemek için nesne odaklı bir model sağlar.
* Tüm dillerin türlerle çalışma geldiğinde izlenmesi gereken bir kurallar kümesi tanımlayın.
* Uygulama geliştirmede kullanılan temel ilkel türleri içeren bir kitaplık sağlayın (örneğin,, `Boolean` `Byte` `Char` vb.)

CTS, desteklenmesi gereken iki ana tür türünü tanımlar: başvuru ve değer türleri. Adları tanımlarına işaret.

Başvuru türlerinin nesneleri, nesnenin gerçek değerine bir başvuru ile temsil edilir; Buradaki bir başvuru C/C++ işaretçisine benzer. Yalnızca nesnelerin değerlerinin olduğu bir bellek konumunu ifade eder. Bu türlerin nasıl kullanıldığına ilişkin bir etkisi vardır. Bir değişkene bir başvuru türü atarsanız ve sonra bu değişkeni bir yönteme geçirirseniz, nesne üzerindeki tüm değişiklikler ana nesneye yansıtılır; kopyalama yok.

Değer türleri, nesnelerin değerleriyle temsil edildiği tersidir. Bir değişkene değer türü atarsanız, aslında nesnenin bir değerini kopyalarsınız.

CTS, her biri belirli semantiklerine ve kullanımına sahip birkaç tür kategorisini tanımlar:

* Sınıflar
* Yapılar
* Numaralandırmalar
* Arabirimler
* Temsilciler

CTS Ayrıca, erişim değiştiricileri, geçerli tür üyeleri nedir, devralma ve aşırı yükleme çalışmaları vb. gibi türlerin diğer özelliklerini de tanımlar. Ne yazık ki, bunlardan herhangi birinin derinlemesine olması buna benzer bir giriş makalesi kapsamının ötesinde, ancak bu konuları ele alan daha ayrıntılı içeriklere yönelik bağlantılar için son sırada [daha fazla kaynak](#more-resources) bölümüne başvurabilirsiniz.

## <a name="common-language-specification"></a>Ortak Dil Belirtimi

Tam birlikte çalışabilirlik senaryolarını etkinleştirmek için, kodda oluşturulan tüm nesnelerin, kendilerini kullanan dillerde ( _çağıranları_) bir miktar ortak olması gerekir. Çok sayıda farklı dil olduğundan, .NET **ortak dil belirtimi** (CLS) adlı bir konuda bu ortak özellikleri belirtti. CLS, birçok ortak uygulamanın gerektirdiği bir özellik kümesini tanımlar. Ayrıca, desteklenmesi gereken özellikler konusunda .NET üzerine uygulanan tüm diller için bir tarif sıralaması sağlar.

CLS, CTS 'nin bir alt kümesidir. Bu, CLS kuralları daha sıkı olmadığı takdirde CTS 'deki tüm kuralların CLS için de uygulandığı anlamına gelir. Bir bileşen yalnızca CLS 'daki kurallar kullanılarak derlendiğinden, diğer bir deyişle, API 'sinde yalnızca CLS özelliklerini kullanıma sunarsa, **CLS uyumlu** olarak kabul edilir. Örneğin, `<framework-librares>` .net üzerinde desteklenen dillerin tümünde çalışması gerektiğinden, CLS uyumludur.

CLS 'deki tüm özelliklere genel bir bakış almak için aşağıdaki [kaynaklar](#more-resources) bölümündeki belgelere başvurabilirsiniz.

## <a name="more-resources"></a>Diğer kaynaklar

* [Ortak tür sistemi](./base-types/common-type-system.md)
* [Ortak Dil Belirtimi](language-independence-and-language-independent-components.md)
