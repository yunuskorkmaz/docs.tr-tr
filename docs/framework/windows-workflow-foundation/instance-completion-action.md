---
description: 'Daha fazla bilgi edinin: örnek tamamlama eylemi'
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 84405ca9869369e4fe00b0049d628671a79a9f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792693"
---
# <a name="instance-completion-action"></a><span data-ttu-id="50db7-103">Örnek Tamamlama Eylemi</span><span class="sxs-lookup"><span data-stu-id="50db7-103">Instance Completion Action</span></span>

<span data-ttu-id="50db7-104">SQL Iş akışı örneği deposunun **örnek tamamlama eylemi** özelliği, iş akışı örneklerinin verilerin ve meta verilerinin, örnekler tamamlandıktan sonra kalıcılık veritabanından silinip silinmeyeceğini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="50db7-104">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="50db7-105">Bu özellik için izin verilen değerler **DeleteAll** ve **deletenoin**' dir.</span><span class="sxs-lookup"><span data-stu-id="50db7-105">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="50db7-106">Aşağıdaki listede bu seçenekler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="50db7-106">The following list describes these options:</span></span>

- <span data-ttu-id="50db7-107">**DeleteAll (varsayılan).**</span><span class="sxs-lookup"><span data-stu-id="50db7-107">**DeleteAll (default).**</span></span> <span data-ttu-id="50db7-108">Özelliğin değeri DeleteAll olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra kalıcılık veritabanından silinir.</span><span class="sxs-lookup"><span data-stu-id="50db7-108">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="50db7-109">**Deletenoşeyi.**</span><span class="sxs-lookup"><span data-stu-id="50db7-109">**DeleteNothing.**</span></span> <span data-ttu-id="50db7-110">Özelliğin değeri Deletenoto olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra bile Kalıcılık veritabanında tutulur.</span><span class="sxs-lookup"><span data-stu-id="50db7-110">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="50db7-111">Örneklerin tamamlanmasının ardından örnek durum bilgilerinin tutulması, kalıcılık veritabanının boyutunun büyümesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="50db7-111">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="50db7-112">Veritabanının boyutu, Kalıcılık alt sisteminin daha uzun sürdüğü veritabanı işlemlerini büyüdüğü için, performans ihtiyaçlarınızı karşılayan düzeyde Hizmetleri gerçekleştirmek üzere Kalıcılık veritabanından örnek durum bilgilerini düzenli aralıklarla temizlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="50db7-112">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
