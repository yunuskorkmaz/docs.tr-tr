---
title: Karma Kodlarla Veri Bütünlüğünü Sağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528558"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="c3bdb-102">Karma Kodlarla Veri Bütünlüğünü Sağlama</span><span class="sxs-lookup"><span data-stu-id="c3bdb-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="c3bdb-103">Bir karma değer veri benzersiz olarak tanımlayan sabit uzunlukta sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="c3bdb-104">Kullanıldıkları ile dijital imzalar için karma değerlerini büyük miktarlarda veri çok daha küçük sayısal değer olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="c3bdb-105">Bir karma değer değerinden daha büyük bir değer imzalama daha verimli bir şekilde oturum açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="c3bdb-106">Karma değerleri, güvenli kanal gönderilen verilerin bütünlüğünü doğrulamak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="c3bdb-107">Veri değiştirilmiş olup olmadığını belirlemek için gönderildiği gibi veri karma değeri için alınan veri karma değeri karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="c3bdb-108">Bu konu, oluşturmak ve karma kodları sınıflarını kullanarak doğrulamak açıklar <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="c3bdb-109">Bir karma oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3bdb-109">Generating a Hash</span></span>  
 <span data-ttu-id="c3bdb-110">Yönetilen karma sınıflar, bir bayt dizisi ya da yönetilen akış nesnesi karma.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="c3bdb-111">Aşağıdaki örnek, bir dize için bir karma değer oluşturmak için SHA1 karma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="c3bdb-112">Örnekte <xref:System.Text.UnicodeEncoding> kullanarak karma bir bayt dizisi dize dönüştürmek için sınıf <xref:System.Security.Cryptography.SHA1Managed> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="c3bdb-113">Karma değeri daha sonra konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="c3bdb-114">Bu kod, konsola aşağıdaki dizeyi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c3bdb-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="c3bdb-115">Bir karma değer doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="c3bdb-115">Verifying a Hash</span></span>  
 <span data-ttu-id="c3bdb-116">Veri bütünlüğünü belirlemek için bir karma değer karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="c3bdb-117">Genellikle, verileri belirli bir süre sonunda karma uygulanır ve karma değeri herhangi bir şekilde korunur.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="c3bdb-118">Daha sonra verileri yeniden karma ve korumalı değerine karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="c3bdb-119">Karma değerleri eşleşirse, veri değiştirilmediğinden.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="c3bdb-120">Değerler eşleşmiyorsa veriler bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="c3bdb-121">Bu sistem çalışmaya korumalı karma şifrelenmiş veya güvenilmeyen taraflardan gizli tutulduğundan.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="c3bdb-122">Aşağıdaki örnek yeni bir karma değer dizeye önceki karma değerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="c3bdb-123">Bu örnekte, karma değerleri ait her baytın döngüye girer ve bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="c3bdb-124">Bu kod, iki karma değerleri eşleşirse, konsola aşağıdaki görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c3bdb-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="c3bdb-125">Bunlar eşleşmiyorsa, kod şunları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c3bdb-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3bdb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3bdb-126">See also</span></span>

- [<span data-ttu-id="c3bdb-127">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c3bdb-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
