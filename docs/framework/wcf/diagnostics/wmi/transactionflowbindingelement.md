---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 577502d1cd3d81784cb9b1eb3b249376b8ffa6b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234901"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="f2e0f-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2e0f-102">TransactionFlowBindingElement</span></span>

<span data-ttu-id="f2e0f-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2e0f-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e0f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2e0f-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f2e0f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f2e0f-105">Methods</span></span>  

 <span data-ttu-id="f2e0f-106">TransactionFlowBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f2e0f-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2e0f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f2e0f-107">Properties</span></span>  

 <span data-ttu-id="f2e0f-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f2e0f-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="f2e0f-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="f2e0f-109">IssuedTokens</span></span>  

 <span data-ttu-id="f2e0f-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f2e0f-110">Data type: string</span></span>  
  
 <span data-ttu-id="f2e0f-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f2e0f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2e0f-112">Verilen bir güvenlik belirteçleri üst bilgisi için gereksinimi belirtir (WS-Trust ' den IssuedTokens).</span><span class="sxs-lookup"><span data-stu-id="f2e0f-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="f2e0f-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f2e0f-113">TransactionProtocol</span></span>  

 <span data-ttu-id="f2e0f-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f2e0f-114">Data type: string</span></span>  
  
 <span data-ttu-id="f2e0f-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f2e0f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2e0f-116">İşlemleri Flow için hizmet tarafından kullanılan işlemler protokolü.</span><span class="sxs-lookup"><span data-stu-id="f2e0f-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="f2e0f-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="f2e0f-117">Transactions</span></span>  

 <span data-ttu-id="f2e0f-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f2e0f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2e0f-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f2e0f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2e0f-120">Gelen işlemin desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2e0f-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2e0f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2e0f-121">Requirements</span></span>  
  
|<span data-ttu-id="f2e0f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f2e0f-122">MOF</span></span>|<span data-ttu-id="f2e0f-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f2e0f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2e0f-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f2e0f-124">Namespace</span></span>|<span data-ttu-id="f2e0f-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f2e0f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2e0f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e0f-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
