---
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044338"
---
# <a name="instance-completion-action"></a><span data-ttu-id="0ed6d-102">Örnek Tamamlama Eylemi</span><span class="sxs-lookup"><span data-stu-id="0ed6d-102">Instance Completion Action</span></span>

<span data-ttu-id="0ed6d-103">SQL Iş akışı örneği deposunun **örnek tamamlama eylemi** özelliği, iş akışı örneklerinin verilerin ve meta verilerinin, örnekler tamamlandıktan sonra kalıcılık veritabanından silinip silinmeyeceğini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="0ed6d-104">Bu özellik için izin verilen değerler **DeleteAll** ve **deletenoin**' dir.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="0ed6d-105">Aşağıdaki listede bu seçenekler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0ed6d-105">The following list describes these options:</span></span>

- <span data-ttu-id="0ed6d-106">**DeleteAll (varsayılan).**</span><span class="sxs-lookup"><span data-stu-id="0ed6d-106">**DeleteAll (default).**</span></span> <span data-ttu-id="0ed6d-107">Özelliğin değeri DeleteAll olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra kalıcılık veritabanından silinir.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="0ed6d-108">**Deletenoşeyi.**</span><span class="sxs-lookup"><span data-stu-id="0ed6d-108">**DeleteNothing.**</span></span> <span data-ttu-id="0ed6d-109">Özelliğin değeri Deletenoto olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra bile Kalıcılık veritabanında tutulur.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="0ed6d-110">Örneklerin tamamlanmasının ardından örnek durum bilgilerinin tutulması, kalıcılık veritabanının boyutunun büyümesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="0ed6d-111">Veritabanının boyutu, Kalıcılık alt sisteminin daha uzun sürdüğü veritabanı işlemlerini büyüdüğü için, hizmet durumlarını karşılayan bir düzeyde gerçekleştirmek için, kalıcılık veritabanından örnek durum bilgilerini düzenli aralıklarla temizlemeniz gerekir. performans ihtiyaçları.</span><span class="sxs-lookup"><span data-stu-id="0ed6d-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
