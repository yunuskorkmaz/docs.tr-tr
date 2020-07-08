---
title: MailAddressParser sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051356"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="6bc74-102">MailAddressParser sınıfı</span><span class="sxs-lookup"><span data-stu-id="6bc74-102">MailAddressParser class</span></span>

<span data-ttu-id="6bc74-103">RFC 2822 ' de açıklandığı gibi e-posta adreslerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="6bc74-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="6bc74-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="6bc74-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="6bc74-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bc74-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6bc74-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6bc74-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="6bc74-107">ParseAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc74-107">ParseAddress method</span></span>

<span data-ttu-id="6bc74-108">Belirtilen dizeden tek bir e-posta adresini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="6bc74-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="6bc74-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bc74-109">Parameters</span></span>

<span data-ttu-id="6bc74-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6bc74-110">`data` <xref:System.String></span></span>

<span data-ttu-id="6bc74-111">Ayrıştırılacak bir e-posta adresi içeren dize.</span><span class="sxs-lookup"><span data-stu-id="6bc74-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="6bc74-112">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="6bc74-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="6bc74-113">Geçerli bir e-posta adresi.</span><span class="sxs-lookup"><span data-stu-id="6bc74-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="6bc74-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="6bc74-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="6bc74-115">E-posta adresi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="6bc74-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bc74-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bc74-116">Requirements</span></span>

<span data-ttu-id="6bc74-117">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6bc74-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6bc74-118">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="6bc74-118">**Assembly:** System (in System.dll)</span></span>
