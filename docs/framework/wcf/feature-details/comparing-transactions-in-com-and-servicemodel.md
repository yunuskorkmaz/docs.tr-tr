---
title: "COM+ ve ServiceModel İşlemlerini Karşılaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="fea3e-102">COM+ ve ServiceModel İşlemlerini Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fea3e-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="fea3e-103">Bu konuda işlem COM + kullanarak hizmet davranışına benzetmek nasıl ele alınmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] öznitelikleri <xref:System.ServiceModel> ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fea3e-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="fea3e-104">COM + ServiceModel öznitelikleri kullanarak öykünmesini yapma</span><span class="sxs-lookup"><span data-stu-id="fea3e-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="fea3e-105">Aşağıdaki tabloda karşılaştırır <xref:System.EnterpriseServices.TransactionOption> numaralandırması oluşturmak için kullanılan bir `EnterpriseServices` işlem ve nasıl bunlar için bağıntısını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öznitelikleri <xref:System.ServiceModel> ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fea3e-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="fea3e-106">COM + özniteliği</span><span class="sxs-lookup"><span data-stu-id="fea3e-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="fea3e-107">öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="fea3e-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="fea3e-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="fea3e-108">RequiresNew</span></span>|<span data-ttu-id="fea3e-109"><xref:System.ServiceModel.TransactionFlowAttribute>ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="fea3e-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="fea3e-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `true`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="fea3e-111">`TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="fea3e-112">Gerekli</span><span class="sxs-lookup"><span data-stu-id="fea3e-112">Required</span></span>|<span data-ttu-id="fea3e-113"><xref:System.ServiceModel.TransactionFlowAttribute>ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span><span class="sxs-lookup"><span data-stu-id="fea3e-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="fea3e-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `true`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="fea3e-115">`TransactionFlow` Bağlama öğesi içinde özniteliktir `true`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="fea3e-116">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="fea3e-116">Supported</span></span>|<span data-ttu-id="fea3e-117">Doğrudan bir eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="fea3e-117">There is no direct equivalent.</span></span> <span data-ttu-id="fea3e-118">İçin belirtilen davranışı genel olarak, benimsemeyi `Required` yerine.</span><span class="sxs-lookup"><span data-stu-id="fea3e-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="fea3e-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="fea3e-119">NotSupported</span></span>|<span data-ttu-id="fea3e-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `false`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="fea3e-121">`TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.</span><span class="sxs-lookup"><span data-stu-id="fea3e-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="fea3e-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="fea3e-122">Disabled</span></span>|<span data-ttu-id="fea3e-123">Doğrudan bir eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="fea3e-123">There is no direct equivalent.</span></span> <span data-ttu-id="fea3e-124">İçin belirtilen davranışı genel olarak, benimsemeyi `NotSupported` yerine.</span><span class="sxs-lookup"><span data-stu-id="fea3e-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|
