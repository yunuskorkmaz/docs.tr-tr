---
title: Azure için Cloud Native .NET Uygulamalarını Temel Alma
description: Azure'un kapsayıcıları, mikro hizmetler ve sunucusuz özelliklerinden yararlanan bulut tasimi uygulamaları oluşturma kılavuzu.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989070"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Azure için Cloud Native .NET Uygulamalarını Temel Alma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![kapak resmi](./media/cover.png)

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif &copy; Hakkı 2019 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.

Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

Yazar:

> **Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Baş Bulut Sistemi Mimar / IP Mimar - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)

Katılımcılar ve Gözden Geçirenler:

> **Cesar De la Torre**, Baş Program Yöneticisi, .NET ekibi, Microsoft
>
> **Nish Anıl**, Sr. Program Yöneticisi, .NET ekibi, Microsoft

Editörler:

> **Maira Wenzel**, Sr. İçerik Geliştirici, .NET ekibi, Microsoft

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalı?

Bu kılavuzun hedef kitlesi ağırlıklı olarak geliştiriciler, geliştirme yol gösterici ve bulut için tasarlanmış uygulamaların nasıl inşa edilebildiğini öğrenmek isteyen mimarlardır.

İkinci bir hedef kitle, bulut açi tabanlı bir yaklaşım kullanarak uygulamalarını oluşturup oluşturmayacağını seçmeyi planlayan teknik karar vericilerdir.

## <a name="how-you-can-use-this-guide"></a>Bu kılavuzu nasıl kullanabilirsiniz?

Bu kılavuz, bulut ayarı tanımlayan ve bulut adajilkeleri ve teknolojileri kullanılarak oluşturulmuş bir başvuru uygulaması sunarak başlar. Bu ilk iki bölümün ötesinde, kitabın geri kalanı bulut tabanlı uygulamaların çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılmıştır. Bulut ait yaklaşımlar hakkında bilgi edinmek için bu bölümlerden herhangi biri için atlayabilirsiniz:

- Veri ve veri erişimi
- Kimlik doğrulaması desenleri
- Ölçekleme ve ölçeklenebilirlik
- Uygulama esnekliği
- İzleme ve sistem durumu
- Kimlik ve güvenlik
- DevOps

Bu kılavuz hem PDF formunda hem de çevrimiçi olarak mevcuttur. Bu konuların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu belgeyi veya çevrimiçi sürümüne bağlantılar iletmekten çekinmeyin. Bu konuların çoğu, temel ilke ve örüntülerin tutarlı bir şekilde anlaşılmasının yanı sıra, bu konularla ilgili kararlarda yer alan dengelerden yararlanır. Bu belge ile amacımız, takımları ve liderlerini, uygulamalarının mimarisi, gelişimi ve barındırması için bilinçli kararlar almak için ihtiyaç duydukları bilgilerle donatmaktır.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
