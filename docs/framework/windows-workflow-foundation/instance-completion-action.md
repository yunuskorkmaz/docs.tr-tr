---
title: "Örnek tamamlama eylemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a>Örnek tamamlama eylemi
**Örneği tamamlama eylem** SQL iş akışı örneği deposunun özelliği veri ve meta veriler iş akışı örneklerinin silindiğinden olup olmadığını Kalıcılık veritabanından örnekleri tamamlandıktan sonra belirtmenize olanak sağlar. Bu özellik için izin verilen değerler **DeleteAll** ve **DeleteNothing**. Aşağıdaki listede, bu seçenekler açıklanmaktadır:  
  
-   **DeleteAll (varsayılan).** Özelliğinin değeri için DeleteAll ayarlarsanız veri ve meta veriler iş akışı örnekleri silinir Kalıcılık veritabanından örnekleri tamamlandıktan sonra.  
  
-   **DeleteNothing.** Özelliğinin değeri için DeleteNothing ayarlarsanız veri ve meta veriler iş akışı örneklerinin tutulur Kalıcılık veritabanında örnekleri bile tamamlandıktan sonra.  
  
    > [!CAUTION]
    >  Örnekleri tamamlanmış nedenler sonra örnek durum bilgisi Kalıcılık boyutları büyürken veritabanına kalmasını sağlar. Veritabanının boyutu Kalıcılık alt sistemi gerçekleştirir veritabanı işlemleri büyüdükçe örneği durumu bilgileri düzenli aralıklarla karşılamak düzeyde performans hizmetleri sağlamak için Kalıcılık veritabanından temizlemek gereken şekilde, uzun, Performans gerekiyor.
