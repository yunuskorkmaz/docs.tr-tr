---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: 1607c1bbcc9bbb3c9fe19840a2827aa5ea083728
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614011"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Azure için Cloud Native .NET uygulamaları tasarlama

![kapak resmi](./media/cover.png)

**SÜRÜM v. 1.0**

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı &copy; 2020 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve https://www.microsoft.com "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

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

Edit

> **Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft

## <a name="version"></a>Sürüm

Bu kılavuz, .NET Core 3,1 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirme ile birlikte **.net core 3,1** sürümünü kapsayacak şekilde yazılmıştır.

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

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
