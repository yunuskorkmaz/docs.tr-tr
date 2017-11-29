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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d1e0f367ef167e5bf47d0936e0b3200ca7dbe19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="instance-completion-action"></a><span data-ttu-id="52c70-102">Örnek tamamlama eylemi</span><span class="sxs-lookup"><span data-stu-id="52c70-102">Instance Completion Action</span></span>
<span data-ttu-id="52c70-103">**Örneği tamamlama eylem** SQL iş akışı örneği deposunun özelliği veri ve meta veriler iş akışı örneklerinin silindiğinden olup olmadığını Kalıcılık veritabanından örnekleri tamamlandıktan sonra belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52c70-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="52c70-104">Bu özellik için izin verilen değerler **DeleteAll** ve **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="52c70-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="52c70-105">Aşağıdaki listede, bu seçenekler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="52c70-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="52c70-106">**DeleteAll (varsayılan).**</span><span class="sxs-lookup"><span data-stu-id="52c70-106">**DeleteAll (default).**</span></span> <span data-ttu-id="52c70-107">Özelliğinin değeri için DeleteAll ayarlarsanız veri ve meta veriler iş akışı örnekleri silinir Kalıcılık veritabanından örnekleri tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="52c70-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="52c70-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="52c70-108">**DeleteNothing.**</span></span> <span data-ttu-id="52c70-109">Özelliğinin değeri için DeleteNothing ayarlarsanız veri ve meta veriler iş akışı örneklerinin tutulur Kalıcılık veritabanında örnekleri bile tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="52c70-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="52c70-110">Örnekleri tamamlanmış nedenler sonra örnek durum bilgisi Kalıcılık boyutları büyürken veritabanına kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="52c70-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="52c70-111">Veritabanının boyutu Kalıcılık alt sistemi gerçekleştirir veritabanı işlemleri büyüdükçe örneği durumu bilgileri düzenli aralıklarla karşılamak düzeyde performans hizmetleri sağlamak için Kalıcılık veritabanından temizlemek gereken şekilde, uzun, Performans gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="52c70-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
