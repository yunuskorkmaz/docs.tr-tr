---
title: MailAddressParser sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990421"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="9abc4-102">MailAddressParser sınıfı</span><span class="sxs-lookup"><span data-stu-id="9abc4-102">MailAddressParser class</span></span>

<span data-ttu-id="9abc4-103">RFC 2822 ' de açıklandığı gibi e-posta adreslerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9abc4-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="9abc4-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="9abc4-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="9abc4-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9abc4-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9abc4-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9abc4-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="9abc4-107">ParseAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abc4-107">ParseAddress method</span></span>

<span data-ttu-id="9abc4-108">Belirtilen dizeden tek bir e-posta adresini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9abc4-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="9abc4-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9abc4-109">Parameters</span></span>

<span data-ttu-id="9abc4-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="9abc4-110">`data` <xref:System.String></span></span>

<span data-ttu-id="9abc4-111">Ayrıştırılacak bir e-posta adresi içeren dize.</span><span class="sxs-lookup"><span data-stu-id="9abc4-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="9abc4-112">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="9abc4-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="9abc4-113">Geçerli bir e-posta adresi.</span><span class="sxs-lookup"><span data-stu-id="9abc4-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="9abc4-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="9abc4-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="9abc4-115">E-posta adresi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="9abc4-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="9abc4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9abc4-116">Requirements</span></span>

<span data-ttu-id="9abc4-117">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9abc4-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9abc4-118">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="9abc4-118">**Assembly:** System (in System.dll)</span></span>
