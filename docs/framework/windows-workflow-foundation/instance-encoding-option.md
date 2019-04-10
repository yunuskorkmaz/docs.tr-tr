---
title: Örnek Kodlama Seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315627"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="0443c-102">Örnek Kodlama Seçeneği</span><span class="sxs-lookup"><span data-stu-id="0443c-102">Instance Encoding Option</span></span>
<span data-ttu-id="0443c-103">**Örnek kodlama seçeneği** SQL iş akışı örneği Store özelliğini SQL kalıcı bir sağlayıcı kaydetmeden önce GZip algoritmasıyla iş akışı örneği durumu bilgileri sıkıştırma belirtmenize olanak sağlar Kalıcılık veritabanı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="0443c-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="0443c-104">Bu özellik için izin verilen değerler şunlardır: GZip ve yok.</span><span class="sxs-lookup"><span data-stu-id="0443c-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="0443c-105">Varsayılan değer, Yok'tur.</span><span class="sxs-lookup"><span data-stu-id="0443c-105">The default value is None.</span></span> <span data-ttu-id="0443c-106">Aşağıdaki listede, bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0443c-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="0443c-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="0443c-107">**GZip**.</span></span> <span data-ttu-id="0443c-108">Kalıcılık veritabanı durumu bilgileri devam ettirmeden önce GZip algoritmasıyla durum bilgilerini kalıcı bir sağlayıcı kodlar.</span><span class="sxs-lookup"><span data-stu-id="0443c-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="0443c-109">**Hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="0443c-109">**None**.</span></span> <span data-ttu-id="0443c-110">Kalıcı bir sağlayıcı bilgileri Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlamaz.</span><span class="sxs-lookup"><span data-stu-id="0443c-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="0443c-111">İş akışı örneği durumu bilgileri kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve iş akışı hizmeti konağı olduğu bir bilgisayardan farklı bir bilgisayara ağ üzerinde veritabanının bulunduğu, ayrıca ağ kullanımını azaltır çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0443c-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="0443c-112">Genel bir kılavuz ayarlamaktır **örnek kodlama seçeneği** özelliğini **hiçbiri** iş akışı örneği durumu küçükse.</span><span class="sxs-lookup"><span data-stu-id="0443c-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
