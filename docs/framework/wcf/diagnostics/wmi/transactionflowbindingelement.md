---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188033"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="29e1f-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="29e1f-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="29e1f-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="29e1f-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29e1f-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="29e1f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="29e1f-105">Methods</span></span>  
 <span data-ttu-id="29e1f-106">TransactionFlowBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="29e1f-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29e1f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="29e1f-107">Properties</span></span>  
 <span data-ttu-id="29e1f-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="29e1f-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="29e1f-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="29e1f-109">IssuedTokens</span></span>  
 <span data-ttu-id="29e1f-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="29e1f-110">Data type: string</span></span>  
  
 <span data-ttu-id="29e1f-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="29e1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29e1f-112">Verilen güvenlik belirteçleri başlığı (WS-Trust gelen IssuedTokens) için gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="29e1f-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="29e1f-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="29e1f-113">TransactionProtocol</span></span>  
 <span data-ttu-id="29e1f-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="29e1f-114">Data type: string</span></span>  
  
 <span data-ttu-id="29e1f-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="29e1f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29e1f-116">İşlem akış işlem hizmeti tarafından kullanılan protokol.</span><span class="sxs-lookup"><span data-stu-id="29e1f-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="29e1f-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="29e1f-117">Transactions</span></span>  
 <span data-ttu-id="29e1f-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="29e1f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="29e1f-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="29e1f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29e1f-120">Gelen işlem desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e1f-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e1f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29e1f-121">Requirements</span></span>  
  
|<span data-ttu-id="29e1f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="29e1f-122">MOF</span></span>|<span data-ttu-id="29e1f-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="29e1f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="29e1f-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="29e1f-124">Namespace</span></span>|<span data-ttu-id="29e1f-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29e1f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29e1f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29e1f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
