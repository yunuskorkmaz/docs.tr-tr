---
description: 'Hakkında daha fazla bilgi edinin: TransactionFlowBindingElement'
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 6a96a83c563affdaef01a12d64bc1c13ab2f719e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757143"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="13dbe-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="13dbe-103">TransactionFlowBindingElement</span></span>

<span data-ttu-id="13dbe-104">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="13dbe-104">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13dbe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="13dbe-105">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="13dbe-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="13dbe-106">Methods</span></span>  

 <span data-ttu-id="13dbe-107">TransactionFlowBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="13dbe-107">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="13dbe-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="13dbe-108">Properties</span></span>  

 <span data-ttu-id="13dbe-109">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="13dbe-109">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="13dbe-110">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="13dbe-110">IssuedTokens</span></span>  

 <span data-ttu-id="13dbe-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="13dbe-111">Data type: string</span></span>  
  
 <span data-ttu-id="13dbe-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="13dbe-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13dbe-113">Verilen bir güvenlik belirteçleri üst bilgisi için gereksinimi belirtir (WS-Trust ' den IssuedTokens).</span><span class="sxs-lookup"><span data-stu-id="13dbe-113">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="13dbe-114">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="13dbe-114">TransactionProtocol</span></span>  

 <span data-ttu-id="13dbe-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="13dbe-115">Data type: string</span></span>  
  
 <span data-ttu-id="13dbe-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="13dbe-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13dbe-117">İşlemleri Flow için hizmet tarafından kullanılan işlemler protokolü.</span><span class="sxs-lookup"><span data-stu-id="13dbe-117">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="13dbe-118">İşlemler</span><span class="sxs-lookup"><span data-stu-id="13dbe-118">Transactions</span></span>  

 <span data-ttu-id="13dbe-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="13dbe-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="13dbe-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="13dbe-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13dbe-121">Gelen işlemin desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13dbe-121">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13dbe-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13dbe-122">Requirements</span></span>  
  
|<span data-ttu-id="13dbe-123">MOF</span><span class="sxs-lookup"><span data-stu-id="13dbe-123">MOF</span></span>|<span data-ttu-id="13dbe-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13dbe-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="13dbe-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="13dbe-125">Namespace</span></span>|<span data-ttu-id="13dbe-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="13dbe-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13dbe-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13dbe-127">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
