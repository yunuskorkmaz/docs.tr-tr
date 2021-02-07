---
description: 'Daha fazla bilgi edinin: MailAddressParser sınıfı'
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
ms.openlocfilehash: 5ad534e731e283f5449b3b8cc8e87628716da9b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699772"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="ebc90-103">MailAddressParser sınıfı</span><span class="sxs-lookup"><span data-stu-id="ebc90-103">MailAddressParser class</span></span>

<span data-ttu-id="ebc90-104">RFC 2822 ' de açıklandığı gibi e-posta adreslerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="ebc90-104">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="ebc90-105">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="ebc90-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="ebc90-106">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ebc90-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ebc90-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ebc90-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="ebc90-108">ParseAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebc90-108">ParseAddress method</span></span>

<span data-ttu-id="ebc90-109">Belirtilen dizeden tek bir e-posta adresini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="ebc90-109">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="ebc90-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebc90-110">Parameters</span></span>

<span data-ttu-id="ebc90-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ebc90-111">`data` <xref:System.String></span></span>

<span data-ttu-id="ebc90-112">Ayrıştırılacak bir e-posta adresi içeren dize.</span><span class="sxs-lookup"><span data-stu-id="ebc90-112">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="ebc90-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="ebc90-113">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="ebc90-114">Geçerli bir e-posta adresi.</span><span class="sxs-lookup"><span data-stu-id="ebc90-114">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="ebc90-115">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="ebc90-115">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="ebc90-116">E-posta adresi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="ebc90-116">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebc90-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebc90-117">Requirements</span></span>

<span data-ttu-id="ebc90-118">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ebc90-118">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ebc90-119">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="ebc90-119">**Assembly:** System (in System.dll)</span></span>
