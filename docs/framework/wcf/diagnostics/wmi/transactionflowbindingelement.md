---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641690"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="7ff75-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7ff75-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="7ff75-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7ff75-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ff75-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ff75-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ff75-105">Methods</span></span>  
 <span data-ttu-id="7ff75-106">TransactionFlowBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7ff75-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ff75-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7ff75-107">Properties</span></span>  
 <span data-ttu-id="7ff75-108">TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7ff75-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="7ff75-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="7ff75-109">IssuedTokens</span></span>  
 <span data-ttu-id="7ff75-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7ff75-110">Data type: string</span></span>  
  
 <span data-ttu-id="7ff75-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7ff75-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ff75-112">Verilen güvenlik belirteçleri başlığı (WS-Trust gelen IssuedTokens) için gereksinim belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ff75-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="7ff75-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="7ff75-113">TransactionProtocol</span></span>  
 <span data-ttu-id="7ff75-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7ff75-114">Data type: string</span></span>  
  
 <span data-ttu-id="7ff75-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7ff75-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ff75-116">İşlem akış işlem hizmeti tarafından kullanılan protokol.</span><span class="sxs-lookup"><span data-stu-id="7ff75-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="7ff75-117">İşlemler</span><span class="sxs-lookup"><span data-stu-id="7ff75-117">Transactions</span></span>  
 <span data-ttu-id="7ff75-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7ff75-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7ff75-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7ff75-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ff75-120">Gelen işlem desteklenip desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff75-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff75-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff75-121">Requirements</span></span>  
  
|<span data-ttu-id="7ff75-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7ff75-122">MOF</span></span>|<span data-ttu-id="7ff75-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7ff75-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7ff75-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7ff75-124">Namespace</span></span>|<span data-ttu-id="7ff75-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ff75-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ff75-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff75-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
