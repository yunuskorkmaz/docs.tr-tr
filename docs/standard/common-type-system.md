---
title: Ortak tür sistemi ve ortak dil belirtimi
description: Nasıl ortak tür sistemi (CTS) ve ortak dil belirtimi (CLS), .NET için birden fazla dili desteklemeye mümkün hale öğrenin.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: a6704b09a51a509cb7fbd786f9040454f78cc862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053203"
---
# <a name="common-type-system--common-language-specification"></a>Ortak tür sistemi ve ortak dil belirtimi

Yeniden serbestçe .NET dünyada kullanılan iki terim, aslında bir .NET uygulamasında çok dilde geliştirme nasıl sağladığını anlamak ve nasıl çalıştığını anlamak için önemlidir.

## <a name="common-type-system"></a>Ortak Tür Sistemi

En baştan başlamak için bir .NET uygulaması olduğunu unutmayın _dilden_. Bu yalnızca bir programcı için IL derlenebilir herhangi bir dilde kodunu yazabilirsiniz gelmez. Ayrıca, kendisi üzerinde bir .NET uygulaması arzulanan diğer dillerde yazılmış kod ile etkileşemeyebilirsiniz gerektiği anlamına gelir.

Şeffaf bir şekilde, bunu yapmak için var olan desteklenen tüm türlerini tanımlamak için yaygın bir yolu olacak. Bunun yapılması sorumlu ortak tür sistemi (CTS) nedir budur. Çeşitli şeyler çalışıldı:

* Diller arası yürütme için bir çerçeve oluşturun.
* Bir .NET uygulaması üzerinde çeşitli dillerde uygulama desteklemek için nesne odaklı bir model sağlar.
* Türleriyle çalışmak için söz konusu olduğunda, tüm dillerin izlemesi gereken kural kümesini tanımlar.
* Uygulama geliştirmesinde kullanılan ilkel temel türler içeren bir kitaplık sağlar (gibi `Boolean`, `Byte`, `Char` vs.)

CTS desteklenmesi gereken türleri iki tür tanımlar: başvuru ve değer türleri. Adları için bunların tanımlarının üzerine gelin.

Başvuru türleri nesneleri, nesnenin gerçek değerine bir başvuru tarafından temsil edilir; C/C++'ta bir işaretçi başvuru burada benzer. Yalnızca bir bellek konumuna nesnelerin değerlerinin olduğu anlamına gelir. Bu, bu tür nasıl kullanıldığını üzerinde çok büyük bir etkisi yoktur. Örneğin, bir başvuru türü bir değişkene atayın ve ardından bu değişkeni bir yönteme geçirmek, nesne değişiklikleri ana nesne üzerinde yansıtılır; kopyalamaya yoktur.

Değer bunun tersini de burada nesneleri değerlerine tarafından temsil edilen türleridir. Bir değer türü bir değişkene atarsanız, aslında bir nesnenin değerini kopyalarsınız.

CTS, her biri kendi belirli semantikler ve kullanım türleri çeşitli kategorileri tanımlar:

* Sınıflar
* Yapılar
* Numaralandırmalar
* Arabirimler
* Temsilciler

CTS diğer tüm özellikler gibi geçerli bir tür üyelerini nasıl nedir, erişim değiştiricileri türleri de tanımlar ve devralma çalışır ve benzeri aşırı yükleme. Ne yazık ki giderek ayrıntılı bulunanlardan herhangi biri olarak bunun gibi bir giriş makalesi kapsamı dışında olsa da, başvurabilirsiniz [daha fazla kaynak](#more-resources) bağlantıları bu konuları kapsayan daha kapsamlı bilgi edinmek için son bölümü.

## <a name="common-language-specification"></a>Ortak Dil Belirtimi

Tam birlikte çalışabilirlik senaryoları etkinleştirmek için kod içinde oluşturulan tüm nesneleri bazı ortak özellikler, bunları kullanan dillerde dayanan gerekir (olan kendi _çağıranlar_). Çok sayıda farklı dillerde olduğundan, .NET bu commonalities adlı bir şey belirtilmiş **ortak dil belirtimi** (CLS). CLS birçok yaygın uygulamalar için gerekli özellikler kümesini tanımlar. Ayrıca, bir tür üzerinde .NET desteklemek için gerekenler üzerinde gerçekleştirilen herhangi bir dilde tarif sağlar.

CLS CTS bir alt kümesidir. CLS kural daha katı olmadığı sürece bu cts'deki kurallarının tümü de CLS, uygulamanız anlamına gelir. Bir bileşen içinde CLS kuralları yalnızca kullanılarak derlendi ise diğer bir deyişle, yalnızca kendi API CLS özellikleri sunan, olarak kabul edilir **CLS uyumlu**. Örneğin, `<framework-librares>` tam olarak tüm .NET üzerinde desteklenen dilleri çalışmak ihtiyaç duydukları çünkü CLS uyumludur.

Belgelerde başvurabilirsiniz [daha kaynakları](#more-resources) CLS içinde tüm özelliklerine genel bakış edinmek için aşağıdaki bölümü.

## <a name="more-resources"></a>Daha fazla kaynak

* [Ortak Tür Sistemi](./base-types/common-type-system.md)
* [Ortak dil belirtimi](language-independence-and-language-independent-components.md)
