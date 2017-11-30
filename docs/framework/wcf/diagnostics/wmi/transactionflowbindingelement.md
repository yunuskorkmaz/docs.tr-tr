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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="431d4-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="431d4-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="431d4-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="431d4-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431d4-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="431d4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="431d4-105">Methods</span></span>  
 <span data-ttu-id="431d4-106">TransactionFlowBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="431d4-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="431d4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="431d4-107">Properties</span></span>  
 <span data-ttu-id="431d4-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="431d4-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="431d4-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="431d4-109">IssuedTokens</span></span>  
 <span data-ttu-id="431d4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="431d4-110">Data type: string</span></span>  
  
 <span data-ttu-id="431d4-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="431d4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="431d4-112">Verilen güvenlik belirteçleri üstbilgisi (WS-Trust gelen IssuedTokens) gereksinimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="431d4-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="431d4-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="431d4-113">TransactionProtocol</span></span>  
 <span data-ttu-id="431d4-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="431d4-114">Data type: string</span></span>  
  
 <span data-ttu-id="431d4-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="431d4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="431d4-116">Akış işlemleri için hizmet tarafından kullanılan işlemleri protokol.</span><span class="sxs-lookup"><span data-stu-id="431d4-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="431d4-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="431d4-117">Transactions</span></span>  
 <span data-ttu-id="431d4-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="431d4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="431d4-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="431d4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="431d4-120">Gelen işlemin desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="431d4-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="431d4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="431d4-121">Requirements</span></span>  
  
|<span data-ttu-id="431d4-122">MOF</span><span class="sxs-lookup"><span data-stu-id="431d4-122">MOF</span></span>|<span data-ttu-id="431d4-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="431d4-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="431d4-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="431d4-124">Namespace</span></span>|<span data-ttu-id="431d4-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="431d4-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="431d4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="431d4-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
