---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: ee8c90d63478e444b7d25cb7cbb5c969963d7c63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130937"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Olay Tabanlı Zaman Uyumsuz Desen (EAP)

Eşiş özelliklerini istemci koduna maruz bırakmanın birkaç yolu vardır. Olay tabanlı Asynchronous Pattern, sınıfların eşzamanlı davranış göstermesi için bir yol yazar.  
  
> [!NOTE]
> .NET Framework 4'ten başlayarak, Görev Paralel Kitaplığı asynchronous ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [Görev Tabanlı Eşzamanlı Desen (TAP)](task-based-asynchronous-pattern-tap.md)bakın.
  
## <a name="in-this-section"></a>Bu Bölümde

 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)  
 Olay tabanlı Asynchronous Deseni'nin, çok iş parçacığı tasarımının doğasında bulunan karmaşık sorunların çoğunu gizlerken çok iş parçacığı uygulamalarının avantajlarını nasıl kullanıma sundığını açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-event-based-asynchronous-pattern.md)  
 Eşzamanlı özelliklere sahip bir sınıfı paketlemenin standartlaştırılmış yolunu açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı Asynchronous Deseni'ne göre eşzamanlı özellikleri ortaya çıkarmak için gereksinimleri açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <xref:System.IAsyncResult> [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen desen yerine Olay tabanlı Eşenkron Deseni'ni ne zaman uygulamanız gerektiğini nasıl belirleyeceğinizi açıklar
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı Asynchronous Deseni'ni uygulayan bir bileşenin nasıl oluşturulacağını açıklar. Bileşenin herhangi bir uygulama modeli <xref:System.ComponentModel?displayProperty=nameWithType> altında doğru çalışmasını sağlayan ad alanından yardımcı sınıflar kullanılarak uygulanır.  

 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı Asynchronous Deseni'ni uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı Asynchronous Deseni destekleyen bir bileşenin nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperation> Sınıfı açıklar ve tüm üyelerine bağlantılar alalar.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncOperationManager> Sınıfı açıklar ve tüm üyelerine bağlantılar alalar.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.BackgroundWorker> Bileşeni açıklar ve tüm üyelerine bağlantılar vardır.  
  
## <a name="related-sections"></a>İlgili Bölümler

 [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Eşzamanlı ve paralel işlemler için bir programlama modelini açıklar.  
  
 [İş Parçacığı Oluşturma](../../../docs/standard/threading/index.md)  
 .NET'te çok iş parçacığı özelliklerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../threading/managed-threading-best-practices.md)
- [Olaylar](../events/index.md)
- [Asynchronous Programlama Tasarım Desenleri](index.md)
