---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be4935d74affa227386aa6c63dad13e7e2f7d3dd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877482"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Olay Tabanlı Zaman Uyumsuz Desen (EAP)

İstemci kodu zaman uyumsuz özelliklerini göstermek için çeşitli yollarla vardır. Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranış sunmak sınıflar için bir yol kullanır.  
  
> [!NOTE]
> .NET Framework 4 ile başlayarak, görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar. Daha fazla bilgi için [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>Bu Bölümde

 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)  
 Açıklayan nasıl olay tabanlı zaman uyumsuz desen çok iş parçacıklı uygulamalar avantajları pek çok iş parçacıklı tasarımında devralınan karmaşık sorunların gizleyerek kullanılabilir hale getirir.  
  
 [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-event-based-asynchronous-pattern.md)  
 Zaman uyumsuz özellikler sahip bir sınıf paketlemek için standartlaştırılmış bir yol açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimleri açıklanır.  
  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Ne zaman yerine olay tabanlı zaman uyumsuz desen uygulamak seçmelidir olmadığının nasıl belireneceğini açıklar <xref:System.IAsyncResult> düzeni temsil ettiği [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md)
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturma işlemini açıklar. Yardımcı sınıflarından kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı bileşen herhangi bir uygulama modeli altında düzgün şekilde çalışmasını sağlar.  

 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen kullanan bir istemci oluşturmayı açıklar.
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.ComponentModel.AsyncOperation>  
 Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşen ve tüm üyeleri için bağlantılar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler

 [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Zaman uyumsuz ve paralel işlemler için bir programlama modeli açıklar.  
  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 . NET'te çok iş parçacıklı özelliklerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../threading/managed-threading-best-practices.md)  
- [Olaylar](../events/index.md)  
- [Zaman uyumsuz programlama desenleri](index.md)
