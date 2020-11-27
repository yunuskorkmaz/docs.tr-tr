---
title: Örnek Kodlama Seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279902"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="17817-102">Örnek Kodlama Seçeneği</span><span class="sxs-lookup"><span data-stu-id="17817-102">Instance Encoding Option</span></span>

<span data-ttu-id="17817-103">SQL Iş akışı örneği deposunun **örnek kodlama seçeneği** ÖZELLIĞI, SQL kalıcılık sağlayıcısı 'nın, bilgileri kalıcılık veritabanına kaydetmeden önce gzip algoritmasını kullanarak iş akışı örneği durum bilgilerini sıkıştırmak gerekip gerekmediğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17817-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="17817-104">Bu özellik için izin verilen değerler: GZip ve None.</span><span class="sxs-lookup"><span data-stu-id="17817-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="17817-105">Varsayılan değer, Yok'tur.</span><span class="sxs-lookup"><span data-stu-id="17817-105">The default value is None.</span></span> <span data-ttu-id="17817-106">Aşağıdaki listede bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17817-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="17817-107">**Gzip**.</span><span class="sxs-lookup"><span data-stu-id="17817-107">**GZip**.</span></span> <span data-ttu-id="17817-108">Kalıcılık sağlayıcısı, kalıcılık veritabanındaki durum bilgilerini kalıcı yapmadan önce GZip algoritmasını kullanarak durum bilgilerini kodlar.</span><span class="sxs-lookup"><span data-stu-id="17817-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="17817-109">**Yok**.</span><span class="sxs-lookup"><span data-stu-id="17817-109">**None**.</span></span> <span data-ttu-id="17817-110">Kalıcılık sağlayıcısı, bilgileri kalıcılık veritabanına kaydetmeden önce durum bilgilerini kodlamaz.</span><span class="sxs-lookup"><span data-stu-id="17817-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="17817-111">GZip kullanan iş akışı örneği durum bilgileri, SQL veritabanında bellek tüketimini azaltır ve ayrıca veritabanı, iş akışı hizmeti konağının çalıştığı bilgisayardan ağdaki farklı bir bilgisayarda bulunuyorsa ağ tüketimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="17817-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="17817-112">Genel bir kılavuz, iş akışı örneği durumu küçükse **örnek kodlama seçeneği** özelliğini **none** olarak ayarlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="17817-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
