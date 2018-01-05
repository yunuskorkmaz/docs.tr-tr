---
title: "Ortak tür sistemi & ortak dil belirtimi"
description: "Nasıl ortak tür sistemi (CTS) ve ortak dil belirtimi (CLS), birden fazla dili desteklemek .NET için olası hale öğrenin."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7626b0a6a902465416187b2c09d624dfe9a9773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="common-type-system--common-language-specification"></a>Ortak tür sistemi & ortak dil belirtimi

Yeniden .NET dünyada ücretsiz olarak kullanılan bu iki terimi aslında bir .NET uygulaması birden fazla dil geliştirme nasıl sağladığını anlamak ve nasıl çalıştığını anlamanız için önemli oldukları.

## <a name="common-type-system"></a>Ortak Tür Sistemi

Baştan başlamak için bir .NET uygulaması olduğunu unutmayın _dil belirsiz_. Bu yalnızca bir programcı için IL derlenebilir herhangi bir dilde kendi kod yazabilirsiniz anlamına gelmez. Ayrıca, aynen bir .NET uygulaması kullanılması için diğer dillerde yazılmış kod ile etkileşim kurabilmesi gerektiği anlamına gelir.

Saydam, bunun için var olan tüm desteklenen türlerini tanımlamak için yaygın bir yolu olmalıdır. Ortak tür sistemi (CTS) sorumlu yapılması nedir budur. Çeşitli işlemler yapmak için yapıldı:

*   Diller arası yürütme için bir çerçeve oluşturun.
*   Bir .NET uygulaması üzerinde çeşitli dillerde uygulama desteklemek için bir nesne yönelimli modeli sağlar.
*   Türleriyle çalışmaya geldiğinde, tüm diller izlemeniz gereken kurallar kümesini tanımlar.
*   Uygulama geliştirme kullanılan temel ilkel türler içeren bir kitaplığı belirtin (gibi `Boolean`, `Byte`, `Char` vs.)

CTS iki ana çeşit desteklenmesi gereken türünü tanımlar: başvuru ve değer türleri. Adları tanımlarını için gelin.

Başvuru türleri nesneleri nesnesinin gerçek değer için bir başvuru olarak temsil edilir; C/C++ içinde bir işaretçi başvuru burada benzer. Yalnızca nesnelerin değerlerinin olduğu bir bellek konumunuz anlamına gelir. Bu, bu tür nasıl kullanıldığı hakkında çok büyük bir etkisi yoktur. Örneğin, bir başvuru türü bir değişkene atayın ve sonra bu değişkeni bir yönteme geçirin, nesne değişiklikleri ana nesnede yansıtılır; hiçbir kopyalama yoktur.

Değer bunun tersini de göre bunların değerleri nerede nesneleri temsil edilen türleridir. Bir değişkene bir değer türü atarsanız, nesnenin bir değeri aslında kopyalarsınız.

CTS türleri, her biri kendi belirli semantiği ve kullanım birkaç kategorisi tanımlar:

*   Sınıflar
*   Yapılar
*   Numaralandırmalar
*   Arabirimler
*   Temsilciler

CTS ayrıca tanımlar türlerinin erişim değiştiricileri, geçerli tür üyeleri nasıl nelerdir gibi diğer tüm özellikleri devralma ve çalışır ve benzeri aşırı yüklemesi. Ne yazık ki, giderek bu hiçbirine derin bunun gibi bir giriş makalesi kapsamı dışında olsa da, başvurabilirsiniz [daha fazla kaynak](#more-resources) bu konuları kapsar daha fazla ayrıntılı içeriğe bağlantılar için sonunda bölüm.

## <a name="common-language-specification"></a>Ortak Dil Belirtimi

Tam birlikte çalışabilirlik senaryoları etkinleştirmek için kod içinde oluşturulan tüm nesneler bazı ortak özellikler bunları kullanan dillerde Bel gerekir (olan kendi _arayanlar_). Çok sayıda farklı dillerde olduğundan, .NET bu commonalities olarak adlandırılan şeyin belirtti **ortak dil belirtimi** (CLS). CLS birçok yaygın uygulama tarafından gerekli olan özellikler kümesini tanımlar. Ayrıca, .NET üstünde desteklemek gerekenler üzerinde uygulanan herhangi bir dil için tarif tür sağlar.

CLS CTS alt kümesidir. CLS kural daha katı sürece bu CTS kurallarında tümünün aynı zamanda CLS uygulamak anlamına gelir. Bir bileşenin CLS yalnızca kurallarını kullanarak oluşturulursa, diğer bir deyişle, yalnızca kendi API CLS özellikleri kullanıma sunan, olarak kabul edilir **CLS uyumlu**. Örneğin, `<framework-librares>` tam olarak tüm .NET desteklenen dilleri çalışmak gereksinim duydukları olduğundan CLS uyumlu değil.

Belgelerde başvurabilirsiniz [daha kaynakları](#more-resources) tüm özelliklerine genel bakış CLS almak için aşağıdaki bölümü.

## <a name="more-resources"></a>Daha fazla kaynak

*   [Ortak Tür Sistemi](./base-types/common-type-system.md)
*   [Ortak dil belirtimi](language-independence-and-language-independent-components.md)
