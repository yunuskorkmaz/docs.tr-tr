---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlamanın, birden çok çekirdekte g/ç ve eş zamanlı işlemleri engellemeyi doğrudan işlemesini sağlayan bir anahtar tekniği olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 1570909b7b416eff81dd90a936ff5ed10aad94f1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346080"
---
# <a name="async-overview"></a>Zaman uyumsuz genel bakış

Bu kadar uzun bir süre önce, uygulamalar daha yeni bir BILGISAYAR veya sunucu satın alarak daha hızlı bir şekilde daha hızlı bir şekilde daha hızlı Aslında tersine çevrilir. Cep telefonları, 1 GHz tek çekirdekli ARM yongalarını ve sunucu iş yüklerini VM 'lere geçti. Kullanıcılar hala yanıt veren kullanıcı arabirimi ve işletme sahiplerinin işletmeyle ölçeklendirebilmesini istiyor. Mobil ve buluta geçiş ve > 3B kullanıcıların Internet 'e bağlı bir popülasyonu, yeni bir yazılım desenleri kümesiyle sonuçlanmıştır. 

- İstemci uygulamalarının her zaman açık, her zaman bağlı ve sürekli olarak kullanıcı etkileşimine (örneğin, Touch) yüksek uygulama mağazası derecelendirmelerine sahip olması beklenir!
- Hizmetin, trafiği yukarı ve aşağı doğru şekilde ölçeklendirerek, trafikte ani artışları işlemesi beklenir. 

Zaman uyumsuz programlama, birden çok çekirdekte g/ç ve eş zamanlı işlemleri engellemeyi doğrudan işlemesini sağlayan temel bir tekniktir. .NET,, Visual Basic ve C# F#' de kullanımı kolay, dil düzeyi zaman uyumsuz programlama modelleriyle uygulamalar ve hizmetler için yanıt verme ve elastik hale getirir.

## <a name="why-write-async-code"></a>Zaman uyumsuz kod neden yazılır?

Modern uygulamalar, dosya ve ağ g/ç 'nin kapsamlı bir şekilde kullanılmasını kolaylaştırır. G/ç API 'Leri geleneksel olarak varsayılan olarak engellenerek, zorlu desenler öğrenmek ve kullanmak istemediğiniz müddetçe kötü kullanıcı deneyimleri ve donanım kullanımı ile sonuçlanır. Görev tabanlı zaman uyumsuz API 'Ler ve dil düzeyi zaman uyumsuz programlama modeli, bu modeli tersine çevirir ve daha fazla yeni kavram ile varsayılan olarak zaman uyumsuz yürütmeyi yapar.

Zaman uyumsuz kod aşağıdaki özelliklere sahiptir:

- G/ç isteklerinin dönmesi beklenirken daha fazla isteği işlemek için iş parçacıkları sunarak daha fazla sunucu isteği işler.
- G/ç isteklerini beklerken ve uzun süre çalışan işleri diğer CPU çekirdeğlerine geçirerek Uıto 'ın Kullanıcı arabirimi etkileşimine yanıt vermesini sağlar.
- Daha yeni .NET API 'Lerinin birçoğu zaman uyumsuzdur.
- .NET ' te zaman uyumsuz kod yazmak kolaydır!

## <a name="whats-next"></a>Sırada ne var?

Daha fazla bilgi için bkz. [zaman uyumsuz ayrıntılı](async-in-depth.md) konuları.

[Zaman uyumsuz programlama desenleri](asynchronous-programming-patterns/index.md) konusu, .net 'te desteklenen üç zaman uyumsuz programlama desenlerine genel bakış sağlar:  
  
- [Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)  
  
- [Olay tabanlı zaman uyumsuz model (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)  
  
- [Görev tabanlı zaman uyumsuz model (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme için önerilir)  

Önerilen görev tabanlı programlama modeli hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konusuna bakın.
