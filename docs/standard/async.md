---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eş zamanlı işlemleri işlemek kolaylaştırıyor önemli bir tekniktir nasıl olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627911"
---
# <a name="async-overview"></a>Zaman uyumsuz genel bakış

Bu nedenle zamanlara kadar uygulamaları daha hızlı yalnızca daha yeni bir PC veya sunucuyu ve ardından ilgili eğilim satın alarak durduruldu. Aslında, ters. Cep telefonları, 1 ghz tek çekirdek ARM görünen yongaları ve sunucu iş yükleri Vm'lere geçti. Kullanıcılar hala duyarlı kullanıcı Arabirimi ve işletme sahipleri ile işlerini ölçeklendirmeyi sunucuları istiyorsanız. Geçiş mobil ve Bulut ve İnternet'e bağlı bir popülasyonunu > 3B kullanıcılar yeni bir yazılım desenleri kümesi ile sonuçlandı. 

* İstemci uygulamalar her zaman açık her zaman bağlı ve sürekli etkileşime yanıt vermesini kullanıcı (örneğin, dokunma) ile yüksek app store derecelendirme olması bekleniyor!
* Hizmetler düzgün biçimde yukarı ve aşağı ölçeklendirme tarafından trafiğindeki ani artışları idare beklenir. 

Zaman uyumsuz programlama, engelleme g/ç ve birden çok çekirdek eş zamanlı işlemleri işlemek kolaylaştırıyor önemli bir tekniktir. .NET uygulamaları ve Hizmetleri için hızlı ve kullanımı kolay, dil düzeyinde zaman uyumsuz programlama modelleri ile elastik yeteneği sağlar C#, VB ve F#.

## <a name="why-write-async-code"></a>Zaman uyumsuz kodu neden yazılsın mı?

Modern uygulamalar, dosya ve ağ g/ç yoğun olarak kullanımını olun. G/ç API'leri varsayılan olarak, geleneksel blok öğrenmek ve zorlu desenleri kullanmak istemediğiniz sürece kötü kullanıcı deneyimleri ve donanım kullanımı sonucu. Görev tabanlı zaman uyumsuz API'leri ve dil düzeyi zaman uyumsuz programlama modeli varsayılan öğrenmek için bazı yeni kavramlar ile zaman uyumsuz yürütme yapmadan bu model, ters çevir.

Zaman uyumsuz kod, aşağıdaki özelliklere sahiptir:

* Döndürülecek g/ç istekleri için beklenirken daha fazla isteği işlemek için iş parçacığı oluşturan tarafından daha fazla sunucu isteklerini işler.
* Kullanıcı Arabirimi etkileşimi için g/ç isteği beklerken iş parçacığı oluşturan ve diğer CPU çekirdekleri için uzun süre çalışan iş geçiş göre daha hızlı yanıt verdiğini kullanıcı arabirimleri sağlar.
* Birçok yeni .NET API'lerini uyumsuzdur.
* . NET'te zaman uyumsuz kod yazmayı kolaydır!

## <a name="whats-next"></a>Sırada ne var?

Daha fazla bilgi için [zaman uyumsuz derinlemesine](async-in-depth.md) konu.

[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) konu,. NET'te desteklenen üç zaman uyumsuz programlama desenleri için genel bir bakış sağlar:  
  
- [Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)  
  
- [Olay tabanlı zaman uyumsuz desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)  
  
- [Görev tabanlı zaman uyumsuz desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme projeleri için önerilir)  

Önerilen görev-tabanlı programlama modeli hakkında daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konu.
