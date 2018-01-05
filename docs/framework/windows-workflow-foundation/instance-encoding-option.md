---
title: "Örnek kodlama seçeneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="53366-102">Örnek kodlama seçeneği</span><span class="sxs-lookup"><span data-stu-id="53366-102">Instance Encoding Option</span></span>
<span data-ttu-id="53366-103">**Örneği kodlama seçeneği** özelliği SQL iş akışı örneği deposunun SQL Kalıcılık sağlayıcısı kaydetmeden önce GZIP algoritmasını kullanarak iş akışı örneği durum bilgileri sıkıştırma olup olmadığını belirtmenize olanak sağlar Kalıcılık veritabanına bilgileri.</span><span class="sxs-lookup"><span data-stu-id="53366-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="53366-104">Bu özellik için izin verilen değerler: GZip ve yok.</span><span class="sxs-lookup"><span data-stu-id="53366-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="53366-105">Varsayılan değer, Yok'tur.</span><span class="sxs-lookup"><span data-stu-id="53366-105">The default value is None.</span></span> <span data-ttu-id="53366-106">Aşağıdaki listede, bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53366-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="53366-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="53366-107">**GZip**.</span></span> <span data-ttu-id="53366-108">Kalıcılık sağlayıcı durumu bilgileri Kalıcılık veritabanında devam ettirmeden önce GZIP algoritmasını kullanarak durumu bilgilerini kodlar.</span><span class="sxs-lookup"><span data-stu-id="53366-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="53366-109">**Hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="53366-109">**None**.</span></span> <span data-ttu-id="53366-110">Kalıcılık sağlayıcı bilgilerin Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlayın değil.</span><span class="sxs-lookup"><span data-stu-id="53366-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="53366-111">İş akışı örneği durum bilgilerini kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve veritabanı farklı bir bilgisayarda ağ üzerindeki iş akışı hizmeti ana bilgisayarı olduğu bilgisayardan bulunuyorsa Ayrıca ağ kullanımını azaltır çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="53366-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="53366-112">Genel bir yönerge ayarlamaktır **örneği kodlama seçeneği** özelliğine **hiçbiri** iş akışı örneği durum küçükse.</span><span class="sxs-lookup"><span data-stu-id="53366-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
