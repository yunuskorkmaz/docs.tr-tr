---
description: 'Daha fazla bilgi edinin: örnek kodlama seçeneği'
title: Örnek Kodlama Seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 8cca7fd536673ca99b1014173e172508e3d97b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631170"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="52923-103">Örnek Kodlama Seçeneği</span><span class="sxs-lookup"><span data-stu-id="52923-103">Instance Encoding Option</span></span>

<span data-ttu-id="52923-104">SQL Iş akışı örneği deposunun **örnek kodlama seçeneği** ÖZELLIĞI, SQL kalıcılık sağlayıcısı 'nın, bilgileri kalıcılık veritabanına kaydetmeden önce gzip algoritmasını kullanarak iş akışı örneği durum bilgilerini sıkıştırmak gerekip gerekmediğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="52923-104">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="52923-105">Bu özellik için izin verilen değerler: GZip ve None.</span><span class="sxs-lookup"><span data-stu-id="52923-105">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="52923-106">Varsayılan değer, Yok'tur.</span><span class="sxs-lookup"><span data-stu-id="52923-106">The default value is None.</span></span> <span data-ttu-id="52923-107">Aşağıdaki listede bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52923-107">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="52923-108">**Gzip**.</span><span class="sxs-lookup"><span data-stu-id="52923-108">**GZip**.</span></span> <span data-ttu-id="52923-109">Kalıcılık sağlayıcısı, kalıcılık veritabanındaki durum bilgilerini kalıcı yapmadan önce GZip algoritmasını kullanarak durum bilgilerini kodlar.</span><span class="sxs-lookup"><span data-stu-id="52923-109">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="52923-110">**Yok**.</span><span class="sxs-lookup"><span data-stu-id="52923-110">**None**.</span></span> <span data-ttu-id="52923-111">Kalıcılık sağlayıcısı, bilgileri kalıcılık veritabanına kaydetmeden önce durum bilgilerini kodlamaz.</span><span class="sxs-lookup"><span data-stu-id="52923-111">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="52923-112">GZip kullanan iş akışı örneği durum bilgileri, SQL veritabanında bellek tüketimini azaltır ve ayrıca veritabanı, iş akışı hizmeti konağının çalıştığı bilgisayardan ağdaki farklı bir bilgisayarda bulunuyorsa ağ tüketimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="52923-112">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="52923-113">Genel bir kılavuz, iş akışı örneği durumu küçükse **örnek kodlama seçeneği** özelliğini **none** olarak ayarlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="52923-113">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
