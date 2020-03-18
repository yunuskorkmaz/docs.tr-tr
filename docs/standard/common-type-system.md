---
title: Ortak Tür Sistemi ve Ortak Dil Belirtimi
description: Ortak Tür Sistemi (CTS) ve Ortak Dil Belirtimi'nin (CLS) .NET'in birden çok dili desteklemesini nasıl mümkün kdığını öğrenin.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 8983e456b051ace434fda9f6ed9cf9028c2ec2d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187673"
---
# <a name="common-type-system--common-language-specification"></a>Ortak Tür Sistemi ve Ortak Dil Belirtimi

Yine, .NET dünyasında serbestçe kullanılan iki terim, bir .NET uygulamasının çok dilli gelişimi nasıl sağladığını ve nasıl çalıştığını anlamak için çok önemlidir.

## <a name="common-type-system"></a>Ortak Tür Sistemi

Başından başlamak için, bir .NET _uygulamasının dil agnostik_olduğunu unutmayın. Bu sadece bir programcı IL derlenebilir herhangi bir dilde kendi kod yazabilirsiniz anlamına gelmez. Ayrıca, bir .NET uygulamasında kullanılabilecek diğer dillerde yazılmış kodlarla etkileşimedebilmeleri gerektiği anlamına gelir.

Bunu saydam bir şekilde yapabilmek için, desteklenen tüm türleri tanımlamak için ortak bir yol olması gerekir. Bu, Ortak Tip Sistemi'nin (CTS) yapmaktan sorumlu olduğu şeydir. Birkaç şey yapmak için yapıldı:

* Diller arası yürütme için bir çerçeve kurun.
* .NET uygulamasında çeşitli dillerin uygulanmasını desteklemek için nesne yönelimli bir model sağlayın.
* Türlerle çalışma söz konusu olduğunda tüm dillerin izlemesi gereken bir kural kümesi tanımlayın.
* Uygulama geliştirmede kullanılan temel ilkel türleri içeren bir kitaplık `Boolean` `Byte`sağlayın `Char` (örneğin, , , vb.)

CTS desteklenmesi gereken iki ana tür tanımlar: başvuru ve değer türleri. İsimleri tanımlarını işaret ediyor.

Başvuru türlerinin nesneleri nesnenin gerçek değerine yapılan bir başvuruyla temsil edilir; buradaki bir başvuru C/C++'daki bir işaretçiye benzer. Basitçe nesnelerin değerlerinin bulunduğu bir bellek konumu anlamına gelir. Bu, bu türlerin nasıl kullanıldığı üzerinde derin bir etkiye sahiptir. Bir değişkene bir başvuru türü atar ve bu değişkeni bir yönteme geçirirseniz, örneğin, nesnedeki herhangi bir değişiklik ana nesneye yansıtılır; kopyalama yoktur.

Değer türleri, nesnelerin değerleriyle temsil edildiği tam tersidir. Bir değişkene değer türü atarsanız, aslında nesnenin bir değerini kopyalıyorsunuz.

CTS, her biri kendi semantiklerine ve kullanımına sahip çeşitli tür kategorileri tanımlar:

* Sınıflar
* Yapılar
* Numaralandırmalar
* Arabirimler
* Temsilciler

CTS ayrıca, erişim değiştiriciler, geçerli tür üyeleri nelerdir, devralma ve aşırı yükleme nin nasıl çalıştığı vb. gibi türlerin diğer tüm özelliklerini de tanımlar. Ne yazık ki, bunların herhangi birinin derinliklerine gitmek bu gibi bir giriş makalesinin kapsamı dışındadır, ancak bu konuları kapsayan daha derinlemesine içeriğe bağlantılar için sonunda [daha fazla kaynak](#more-resources) bölümüne danışabilirsiniz.

## <a name="common-language-specification"></a>Ortak Dil Belirtimi

Tam birlikte çalışabilirlik senaryolarını etkinleştirmek için, kod halinde oluşturulan tüm nesnelerin, onları tüketen dillerdeki (arayanlar) bazı ortak ayrıntılara _dayanması_gerekir. Çok sayıda farklı dil olduğundan, .NET **ortak dil belirtimi** (CLS) adı verilen bir şeyde bu ortak noktaları belirtmiştir. CLS, birçok yaygın uygulama tarafından gereken bir dizi özellik tanımlar. Ayrıca, .NET'in üzerine uygulanan herhangi bir dil için, desteklemesi gerekenler için bir tür reçete de sağlar.

CLS CTS bir alt kümesidir. Bu, CLS kuralları daha katı olmadığı sürece CTS'deki tüm kuralların CLS için de geçerli olduğu anlamına gelir. Bir bileşen yalnızca CLS'deki kurallar kullanılarak oluşturulmuşsa, yani yalnızca API'sindeki CLS özelliklerini ortaya çıkarırsa, **CLS uyumlu**olduğu söylenir. Örneğin, CLS `<framework-librares>` uyumludur, çünkü .NET'te desteklenen tüm dillerde çalışmaları gerekir.

CLS'deki tüm özelliklere genel bir bakış için aşağıdaki [Daha Fazla Kaynaklar](#more-resources) bölümündeki belgelere başvurabilirsiniz.

## <a name="more-resources"></a>Diğer kaynaklar

* [Ortak Tür Sistemi](./base-types/common-type-system.md)
* [Ortak Dil Belirtimi](language-independence-and-language-independent-components.md)
