---
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: d68f41a586e44f96c9ca26cf8a142a2782adaa36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662970"
---
# <a name="instance-completion-action"></a><span data-ttu-id="506e1-102">Örnek Tamamlama Eylemi</span><span class="sxs-lookup"><span data-stu-id="506e1-102">Instance Completion Action</span></span>
<span data-ttu-id="506e1-103">**Örnek tamamlama eylemi** özelliğini SQL iş akışı örneği Store verileri ve iş akışı örnekleri meta verilerini silindiğinden olmadığını Kalıcılık veritabanı örnekleri tamamlandıktan sonra belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="506e1-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="506e1-104">Bu özellik için izin verilen değerler **DeleteAll** ve **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="506e1-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="506e1-105">Aşağıdaki listede, bu seçenekler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="506e1-105">The following list describes these options:</span></span>  
  
- <span data-ttu-id="506e1-106">**DeleteAll (varsayılan).**</span><span class="sxs-lookup"><span data-stu-id="506e1-106">**DeleteAll (default).**</span></span> <span data-ttu-id="506e1-107">Özelliğinin değeri için DeleteAll ayarlarsanız, verileri ve iş akışı örnekleri meta verileri silinir Kalıcılık veritabanı örnekleri tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="506e1-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
- <span data-ttu-id="506e1-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="506e1-108">**DeleteNothing.**</span></span> <span data-ttu-id="506e1-109">Özelliğinin değeri için DeleteNothing ayarlarsanız, verileri ve iş akışı örnekleri meta verilerini tutulur Kalıcılık veritabanına örnekleri bile tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="506e1-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="506e1-110">Örnek durum bilgilerini örnekleri tamamlanmış nedenler sonra boyutunu büyütmek için Kalıcılık veritabanı kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="506e1-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="506e1-111">Örnek durum bilgilerini düzenli olarak uygun düzeyde hizmetleri sağlamak için Kalıcılık veritabanından temizlemek gereken şekilde Kalıcılık alt gerçekleştiren veritabanı işlemlerinin veritabanının boyutu büyüdükçe daha uzun olması, Performans gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="506e1-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
