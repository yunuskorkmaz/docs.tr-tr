---
title: .NET geliştiricileri için dadpr
description: .NET geliştiricilerinin Microsoft 'un açık kaynaklı dağıtılmış uygulama çalışma zamanının tam gücünden yararlanmasını ve bu avantajlardan faydalamasını sağlar.
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: 53d5356c8e010f0c4e168a2186d48dd9af369ff6
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096734"
---
# <a name="dapr-for-net-developers"></a>.NET geliştiricileri için dadpr

![kapak resmi](./media/cover.png)

**ÖNIZLEME SÜRÜMÜ**

YAYIMLAYAN

Microsoft Geliştirici bölmesi, .NET ve Azure ınubations ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı &copy; 2021 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> **Ramiz Vettor**, sorumlu bulut çözümü mimarı- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft
>
> **Sander Molenkamp**, sorumlu bulut mimarı/Microsoft MVP- [Sandermolenkamp.com](https://www.sandermolenkamp.com), [Info desteği](https://www.infosupport.com/en/)
>
> **Edwin Van Wijk**, Principal Solution mimarı/Microsoft MVP- [Defaultconstructor.com](https://defaultconstructor.com), [Info desteği](https://www.infosupport.com/en/)

Katılımcılar ve gözden geçirenler:

> **Mark Russinovich**, Azure CTO ve teknik bir, Azure Office CTO, Microsoft
>
> **Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft
>
> **Mark Fussell**, Principal program Manager, Azure ınubations, Microsoft
>
> **Yaron Schneider**, sorumlu yazılım mühendisi, Azure ınubations, Microsoft
>
> **Ori Zohar**, üst düzey Program Yöneticisi, Azure ınubations, Microsoft

Edit

> **David çam**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft

> **Maira Wenzel**, Kıdemli Program Yöneticisi, .NET ekibi, Microsoft

## <a name="version"></a>Sürüm

Bu kılavuz, **Davpr 1,0** sürümünü kapsayacak şekilde yazılmıştır. .NET Core örnekleri, **.net core 3,1**' i temel alır.

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.

İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Bu kılavuz hem [PDF](https://aka.ms/dapr-ebook) form hem de çevrimiçi olarak kullanılabilir. Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin. Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır. Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](foreword.md)
