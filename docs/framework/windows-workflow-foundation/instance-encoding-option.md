---
title: Örnek kodlama seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: cfe45428f546b6f47709c321099efdf7fbb25ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512544"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="f3495-102">Örnek kodlama seçeneği</span><span class="sxs-lookup"><span data-stu-id="f3495-102">Instance Encoding Option</span></span>
<span data-ttu-id="f3495-103">**Örneği kodlama seçeneği** özelliği SQL iş akışı örneği deposunun SQL Kalıcılık sağlayıcısı kaydetmeden önce GZIP algoritmasını kullanarak iş akışı örneği durum bilgileri sıkıştırma olup olmadığını belirtmenize olanak sağlar Kalıcılık veritabanına bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f3495-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="f3495-104">Bu özellik için izin verilen değerler: GZip ve yok.</span><span class="sxs-lookup"><span data-stu-id="f3495-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="f3495-105">Varsayılan değer, Yok'tur.</span><span class="sxs-lookup"><span data-stu-id="f3495-105">The default value is None.</span></span> <span data-ttu-id="f3495-106">Aşağıdaki listede, bu seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3495-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="f3495-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="f3495-107">**GZip**.</span></span> <span data-ttu-id="f3495-108">Kalıcılık sağlayıcı durumu bilgileri Kalıcılık veritabanında devam ettirmeden önce GZIP algoritmasını kullanarak durumu bilgilerini kodlar.</span><span class="sxs-lookup"><span data-stu-id="f3495-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="f3495-109">**Hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="f3495-109">**None**.</span></span> <span data-ttu-id="f3495-110">Kalıcılık sağlayıcı bilgilerin Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlayın değil.</span><span class="sxs-lookup"><span data-stu-id="f3495-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="f3495-111">İş akışı örneği durum bilgilerini kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve veritabanı farklı bir bilgisayarda ağ üzerindeki iş akışı hizmeti ana bilgisayarı olduğu bilgisayardan bulunuyorsa Ayrıca ağ kullanımını azaltır çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f3495-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="f3495-112">Genel bir yönerge ayarlamaktır **örneği kodlama seçeneği** özelliğine **hiçbiri** iş akışı örneği durum küçükse.</span><span class="sxs-lookup"><span data-stu-id="f3495-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
