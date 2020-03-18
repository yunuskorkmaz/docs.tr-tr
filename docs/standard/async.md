---
title: Async Genel Bakış
description: Async programlamanın, engelleme G/Ç ve birden çok çekirdekteki eşzamanlı işlemleri işlemeyi kolaylaştıran önemli bir teknik olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159734"
---
# <a name="async-overview"></a>Async Genel Bakış

O kadar uzun zaman önce, uygulamalar sadece yeni bir PC veya sunucu satın alarak daha hızlı var ve daha sonra bu eğilim durdu. Aslında, tersine döndü. Cep telefonları 1ghz tek çekirdekli ARM yongaları ve sunucu iş yükleri VMs geçişli ile ortaya çıktı. Kullanıcılar hala duyarlı Kullanıcı Bira ve işletme sahipleri kendi iş ile ölçeksunucular istiyorum istiyorum. Mobil ve buluta geçiş ve >3B kullanıcılarının internete bağlı nüfusu yeni bir yazılım kalıpları kümesiile sonuçlandı.

- İstemci uygulamalarının her zaman açık, her zaman bağlı ve yüksek uygulama mağazası derecelendirmeleriyle kullanıcı etkileşimine (örneğin dokunma) sürekli yanıt vermesini bekler!
- Hizmetlerin, incelikle yukarı ve aşağı ölçeklendirerek trafikteki ani artışlarla başa çıkaması bekleniyor.

Async programlama, engelleme G/Ç ve birden çok çekirdek teki eşzamanlı işlemleri işlemeyi kolaylaştıran önemli bir tekniktir. .NET, C#, Visual Basic ve F#'da kullanımı kolay, dil düzeyinde asynchronous programlama modelleri ile uygulamaların ve hizmetlerin duyarlı ve esnek olması için gereken yeteneği sağlar.

## <a name="why-write-async-code"></a>Neden Async Kodu Yaz?

Modern uygulamalar dosya ve ağ G/Ç'yi kapsamlı bir şekilde kullanır. G/Ç API'leri varsayılan olarak engellenir ve zorlu desenleri öğrenmek ve kullanmak istemediğiniz sürece kötü kullanıcı deneyimleri ve donanım kullanımı yla sonuçlanır. Görev tabanlı async API'leri ve dil düzeyindeki asynchronous programlama modeli bu modeli tersine çevirerek, async yürütmeyi öğrenmek için birkaç yeni kavramla varsayılan hale getirir.

Async kodu aşağıdaki özelliklere sahiptir:

- G/Ç isteklerinin geri dönmesini beklerken daha fazla isteği işlemek için iş parçacıkları vererek daha fazla sunucu isteklerini işler.
- G/Ç isteklerini beklerken ve uzun süren çalışmaları diğer CPU çekirdeklerine geçirerek Kullanıcı Araları'nın Kullanıcı Arabirimi etkileşimine iş parçacığı vererek daha duyarlı olmasını sağlar.
- Yeni .NET API'lerinin çoğu eşzamanlıdır.
- .NET'te async kodu yazmak kolaydır!

## <a name="whats-next"></a>Sırada ne var?

Daha fazla bilgi [için, derinlemesine konu yla Ilgili Async konusuna](async-in-depth.md) bakın.

[Asynchronous Programlama Desenleri](asynchronous-programming-patterns/index.md) konusu ,NET'te desteklenen üç eşzamanlı programlama deleline genel bir bakış sağlar:  
  
- [Eşzamanlı Programlama Modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)  
  
- [Olay tabanlı Eşzamanlı Desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)  
  
- [Görev tabanlı Eşzamanlı Desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme için önerilir)  

Önerilen görev tabanlı programlama modeli hakkında daha fazla bilgi için [Görev tabanlı asynchronous programlama](parallel-programming/task-based-asynchronous-programming.md) konusuna bakın.
