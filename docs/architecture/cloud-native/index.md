---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: 24d5c75fc5d2e5623892e8f83daea52553d13765
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507396"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Azure için Cloud Native .NET uygulamaları tasarlama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![kapak resmi](./media/cover.png)

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif &copy; hakkı 2019 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "ticari markalar" https://www.microsoft.com Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> **Ramiz Vettor**, sorumlu bulut sistemi MIMARı/IP mimarı- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft
>
> **Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)

Katılımcılar ve gözden geçirenler:

> **Cesar de La Torre**, sorumlu Program Yöneticisi, .NET ekibi, Microsoft
>
> **Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft
>
> **Jeremy Liksizlik**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft
>
> **Cecil Phillip**, üst düzey bulut Danışmanı, Microsoft

EShopOnContainers hakkında daha fazla bilgi edinin

Edit

> **Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.

İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Bu kılavuz, bulut Native 'i tanımlayarak başlar ve bulut Yerel ilkeleri ve teknolojileri kullanılarak oluşturulan bir başvuru uygulaması ile tanışın. Bu ilk iki bölüm dışında, kitabın geri kalanı, bulut Yerel uygulamalarının çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılır. Aşağıdaki gibi, buluta özgü yaklaşımlar hakkında bilgi edinmek için şu bölümlerden birine atlayabilirsiniz:

- Veri ve veri erişimi
- Kimlik doğrulaması desenleri
- Ölçeklendirme ve ölçeklenebilirlik
- Uygulama dayanıklılığı
- İzleme ve sistem durumu
- Kimlik ve güvenlik
- DevOps

Bu kılavuz hem PDF form hem de çevrimiçi olarak kullanılabilir. Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin. Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır. Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
