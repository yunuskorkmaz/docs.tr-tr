---
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791124"
---
# <a name="instance-completion-action"></a>Örnek Tamamlama Eylemi
**Örnek tamamlama eylemi** özelliğini SQL iş akışı örneği Store verileri ve iş akışı örnekleri meta verilerini silindiğinden olmadığını Kalıcılık veritabanı örnekleri tamamlandıktan sonra belirtmenize olanak sağlar. Bu özellik için izin verilen değerler **DeleteAll** ve **DeleteNothing**. Aşağıdaki listede, bu seçenekler açıklanmaktadır:  
  
- **DeleteAll (varsayılan).** Özelliğinin değeri için DeleteAll ayarlarsanız, verileri ve iş akışı örnekleri meta verileri silinir Kalıcılık veritabanı örnekleri tamamlandıktan sonra.  
  
- **DeleteNothing.** Özelliğinin değeri için DeleteNothing ayarlarsanız, verileri ve iş akışı örnekleri meta verilerini tutulur Kalıcılık veritabanına örnekleri bile tamamlandıktan sonra.  
  
    > [!CAUTION]
    >  Örnek durum bilgilerini örnekleri tamamlanmış nedenler sonra boyutunu büyütmek için Kalıcılık veritabanı kalmasını sağlar. Örnek durum bilgilerini düzenli olarak uygun düzeyde hizmetleri sağlamak için Kalıcılık veritabanından temizlemek gereken şekilde Kalıcılık alt gerçekleştiren veritabanı işlemlerinin veritabanının boyutu büyüdükçe daha uzun olması, Performans gerekiyor.
