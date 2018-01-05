---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b073efc47ccc1708bf4c58153b1001a21eee25f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="d1e6e-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1e6e-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="d1e6e-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1e6e-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1e6e-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d1e6e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d1e6e-105">Methods</span></span>  
 <span data-ttu-id="d1e6e-106">TransactionFlowBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1e6e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d1e6e-107">Properties</span></span>  
 <span data-ttu-id="d1e6e-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d1e6e-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="d1e6e-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="d1e6e-109">IssuedTokens</span></span>  
 <span data-ttu-id="d1e6e-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d1e6e-110">Data type: string</span></span>  
  
 <span data-ttu-id="d1e6e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d1e6e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1e6e-112">Verilen güvenlik belirteçleri üstbilgisi (WS-Trust gelen IssuedTokens) gereksinimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="d1e6e-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="d1e6e-113">TransactionProtocol</span></span>  
 <span data-ttu-id="d1e6e-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d1e6e-114">Data type: string</span></span>  
  
 <span data-ttu-id="d1e6e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d1e6e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1e6e-116">Akış işlemleri için hizmet tarafından kullanılan işlemleri protokol.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="d1e6e-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="d1e6e-117">Transactions</span></span>  
 <span data-ttu-id="d1e6e-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d1e6e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d1e6e-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d1e6e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1e6e-120">Gelen işlemin desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1e6e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1e6e-121">Requirements</span></span>  
  
|<span data-ttu-id="d1e6e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d1e6e-122">MOF</span></span>|<span data-ttu-id="d1e6e-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d1e6e-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d1e6e-124">Namespace</span></span>|<span data-ttu-id="d1e6e-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d1e6e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1e6e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e6e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
