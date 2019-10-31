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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130937"
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
 [Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen <xref:System.IAsyncResult> modeli yerine olay tabanlı zaman uyumsuz model uygulamayı ne zaman kullanacağınızı nasıl belirleyebileceğinizi açıklar
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını açıklar. Bu, bileşenin herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak için <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki yardımcı sınıflar kullanılarak uygulanır.  

 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz model uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz stili destekleyen bir bileşenin nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperation> sınıfını açıklar ve tüm üyelerine bağlantıları vardır.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncOperationManager> sınıfını açıklar ve tüm üyelerine bağlantıları vardır.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.BackgroundWorker> bileşeni tanımlar ve tüm üyelerine bağlantıları vardır.  
  
## <a name="related-sections"></a>İlgili Bölümler

 [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Zaman uyumsuz ve paralel işlemler için bir programlama modeli tanımlar.  
  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 .NET 'teki çoklu iş parçacığı özelliklerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../threading/managed-threading-best-practices.md)
- [Olaylar](../events/index.md)
- [Zaman uyumsuz programlama tasarım desenleri](index.md)
