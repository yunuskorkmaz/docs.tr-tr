---
title: Örnek tamamlama eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513207"
---
# <a name="instance-completion-action"></a>Örnek tamamlama eylemi
**Örneği tamamlama eylem** SQL iş akışı örneği deposunun özelliği veri ve meta veriler iş akışı örneklerinin silindiğinden olup olmadığını Kalıcılık veritabanından örnekleri tamamlandıktan sonra belirtmenize olanak sağlar. Bu özellik için izin verilen değerler **DeleteAll** ve **DeleteNothing**. Aşağıdaki listede, bu seçenekler açıklanmaktadır:  
  
-   **DeleteAll (varsayılan).** Özelliğinin değeri için DeleteAll ayarlarsanız veri ve meta veriler iş akışı örnekleri silinir Kalıcılık veritabanından örnekleri tamamlandıktan sonra.  
  
-   **DeleteNothing.** Özelliğinin değeri için DeleteNothing ayarlarsanız veri ve meta veriler iş akışı örneklerinin tutulur Kalıcılık veritabanında örnekleri bile tamamlandıktan sonra.  
  
    > [!CAUTION]
    >  Örnekleri tamamlanmış nedenler sonra örnek durum bilgisi Kalıcılık boyutları büyürken veritabanına kalmasını sağlar. Veritabanının boyutu Kalıcılık alt sistemi gerçekleştirir veritabanı işlemleri büyüdükçe örneği durumu bilgileri düzenli aralıklarla karşılamak düzeyde performans hizmetleri sağlamak için Kalıcılık veritabanından temizlemek gereken şekilde, uzun, Performans gerekiyor.
