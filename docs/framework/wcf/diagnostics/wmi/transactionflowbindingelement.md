---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: d0311837ebb8112d9492fb548492bcd3e10230e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514582"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="871e5-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="871e5-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="871e5-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="871e5-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="871e5-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="871e5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="871e5-105">Methods</span></span>  
 <span data-ttu-id="871e5-106">TransactionFlowBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="871e5-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="871e5-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="871e5-107">Properties</span></span>  
 <span data-ttu-id="871e5-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="871e5-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="871e5-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="871e5-109">IssuedTokens</span></span>  
 <span data-ttu-id="871e5-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="871e5-110">Data type: string</span></span>  
  
 <span data-ttu-id="871e5-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="871e5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="871e5-112">Verilen güvenlik belirteçleri başlığı (WS-Trust gelen IssuedTokens) için gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="871e5-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="871e5-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="871e5-113">TransactionProtocol</span></span>  
 <span data-ttu-id="871e5-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="871e5-114">Data type: string</span></span>  
  
 <span data-ttu-id="871e5-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="871e5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="871e5-116">İşlem akış işlem hizmeti tarafından kullanılan protokol.</span><span class="sxs-lookup"><span data-stu-id="871e5-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="871e5-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="871e5-117">Transactions</span></span>  
 <span data-ttu-id="871e5-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="871e5-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="871e5-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="871e5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="871e5-120">Gelen işlem desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="871e5-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="871e5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="871e5-121">Requirements</span></span>  
  
|<span data-ttu-id="871e5-122">MOF</span><span class="sxs-lookup"><span data-stu-id="871e5-122">MOF</span></span>|<span data-ttu-id="871e5-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="871e5-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="871e5-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="871e5-124">Namespace</span></span>|<span data-ttu-id="871e5-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="871e5-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="871e5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="871e5-126">See also</span></span>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
