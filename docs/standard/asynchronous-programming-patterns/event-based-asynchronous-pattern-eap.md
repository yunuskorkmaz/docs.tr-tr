---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
description: Uygulama, en iyi uygulamalar, EAP istemcisi uygulama ve daha fazlası gibi .NET 'teki olay tabanlı zaman uyumsuz model (EAP) hakkında makalelerin bağlantılarını inceleyin.
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 03b4d914d72b96b882c774565654c022b145b5f2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768878"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Olay Tabanlı Zaman Uyumsuz Desen (EAP)

İstemci kodunda zaman uyumsuz özellikleri açığa çıkarmak için çeşitli yollar vardır. Olay tabanlı zaman uyumsuz model, sınıfların zaman uyumsuz davranışı sunmak için bir yol sunar.  
  
> [!NOTE]
> .NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>Bu Bölümde

 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)  
 Çok iş parçacıklı tasarımda bulunan karmaşık sorunların çoğunu gizleyerek, olay tabanlı zaman uyumsuz düzenin çoklu iş parçacıklı uygulamaların avantajlarından nasıl yararlanacağını açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-event-based-asynchronous-pattern.md)  
 Zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standartlaştırılmış bir yol tanımlar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Zaman uyumsuz özellikleri olay tabanlı zaman uyumsuz düzene göre gösterme gereksinimlerini açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <xref:System.IAsyncResult> [Zaman uyumsuz programlama MODELI (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen model yerine olay tabanlı zaman uyumsuz model uygulamayı ne zaman kullanacağınızı belirlemeyi açıklar
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını açıklar. Bu, <xref:System.ComponentModel?displayProperty=nameWithType> bileşenin herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak üzere ad alanından yardımcı sınıflar kullanılarak uygulanır.  

 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz model uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz stili destekleyen bir bileşenin nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.ComponentModel.AsyncOperation>  
 Sınıfını açıklar <xref:System.ComponentModel.AsyncOperation> ve tüm üyelerine bağlantıları vardır.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Sınıfını açıklar <xref:System.ComponentModel.AsyncOperationManager> ve tüm üyelerine bağlantıları vardır.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Bileşenini açıklar <xref:System.ComponentModel.BackgroundWorker> ve tüm üyelerine bağlantıları vardır.  
  
## <a name="related-sections"></a>İlgili Bölümler

 [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Zaman uyumsuz ve paralel işlemler için bir programlama modeli tanımlar.  
  
 [İş Parçacığı Oluşturma](../threading/index.md)  
 .NET 'teki çoklu iş parçacığı özelliklerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../threading/managed-threading-best-practices.md)
- [Ekinlikler](../events/index.md)
- [Zaman uyumsuz programlama tasarım desenleri](index.md)
