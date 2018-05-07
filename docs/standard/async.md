---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir yöntem nasıl olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9d612186e1051644e8d4ae9476b8fafd811deb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="async-overview"></a>Zaman uyumsuz genel bakış

Değil kısa süre önce uygulamaları daha hızlı yalnızca daha yeni bir bilgisayarı veya sunucuyu ve sonra bu eğilim satın durduruldu. Aslında, ters. Cep telefonları görünen 1 ghz tek çekirdek ARM yongaları ve sunucu iş yükleri için sanal makineleri geçiş yaptı. Kullanıcılar hala yanıt veren UI ve işletme sahipleri kendi iş ölçeklendirme sunucuları istiyorsanız. Mobil geçişi ve Bulut ve internet'e bağlı bir popülasyonunu > 3B kullanıcıların yeni bir yazılım desenleri kümesi ile sonuçlandı. 

* İstemci uygulamaları her zaman açık her zaman bağlı ve yüksek uygulama mağazası derecelendirmeleri ile (örneğin, dokunma) kullanıcı etkileşimi sürekli duyarlı olması beklenen!
* Hizmetleri düzgün biçimde yukarı ve aşağı doğru ölçeklendirme tarafından artışlarını trafiğinin beklenir. 

Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir tekniktir. .NET uygulamaları ve Hizmetleri için esnek ve kullanımı kolay, dil düzeyi zaman uyumsuz programlama modelleri C#, VB ve F # ile esnek olmasını yeteneği sağlar.

## <a name="why-write-async-code"></a>Neden zaman uyumsuz kod yazmayı?

Modern uygulamalar dosya ve ağ g/ç yoğun olarak kullanımını olun. G/ç API'leri geleneksel olarak varsayılan olarak, blok öğrenmek ve zor desenleri kullanmak istemediğiniz sürece zayıf kullanıcı deneyimleri ve donanım kullanımı sonuçlanır. Görev tabanlı zaman uyumsuz API'leri ve dil düzeyi zaman uyumsuz programlama modeli öğrenmek için birkaç yeni kavram varsayılan zaman uyumsuz yürütme yapmadan bu model, ters çevir.

Zaman uyumsuz kod aşağıdaki özelliklere sahiptir:

* G/ç istekleri döndürmek beklenirken daha fazla isteği işlemek için iş parçacığı oluşturan tarafından daha fazla sunucu isteklerini işler.
* G/ç istekleri için beklenirken UI etkileşim için iş parçacığı oluşturan ve uzun süre çalışan iş diğer CPU çekirdekleri geçiş göre daha iyi yanıt olarak Uı'lar sağlar.
* Birçok yeni .NET API'lerini uyumsuzdur.
* . NET'te zaman uyumsuz kod yazmaya kolaydır!

## <a name="whats-next"></a>Sonraki adım nedir?

Daha fazla bilgi için bkz: [zaman uyumsuz derinlemesine](async-in-depth.md) konu.

[Zaman uyumsuz programlama desenleri](/asynchronous-programming-patterns/index.md) konu .NET içinde desteklenen üç zaman uyumsuz programlama desenleri genel bir bakış sağlar:  
  
-   [Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)  
  
-   [Olay tabanlı zaman uyumsuz desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)  
  
-   [Görev tabanlı zaman uyumsuz desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme projeleri için önerilir)  

Görev tabanlı önerilen programlama modeli hakkında daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konu.
