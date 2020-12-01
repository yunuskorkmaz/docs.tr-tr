---
title: SYSLIB0001 uyarısı
description: Derleme zamanı uyarı SYSLIB0001 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: d275717e22b260d9ceff4fe94993e9a0e6996cf0
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437844"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="9e9c4-103">SYSLIB0001: UTF-7 kodlaması güvenli değil</span><span class="sxs-lookup"><span data-stu-id="9e9c4-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="9e9c4-104">UTF-7 kodlaması artık uygulamalar arasında geniş bir kullanım değildir ve birçok adım artık değişim içinde [kullanımını](https://security.stackexchange.com/a/68609/3573) dengeler.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="9e9c4-105">Ayrıca, UTF-7 kodlu verilerle karşılaşmayı düşünmeyin uygulamalarda [saldırı vektörü olarak da kullanılır](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) .</span><span class="sxs-lookup"><span data-stu-id="9e9c4-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="9e9c4-106">Microsoft, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> hata algılaması sağlamadığı için kullanımını uyarır.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="9e9c4-107">Sonuç olarak, aşağıdaki API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="9e9c4-108">Bu API 'lerin kullanımı, `SYSLIB0001` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="9e9c4-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özelliði</span><span class="sxs-lookup"><span data-stu-id="9e9c4-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="9e9c4-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> Kurucu</span><span class="sxs-lookup"><span data-stu-id="9e9c4-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="9e9c4-111">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="9e9c4-111">Workarounds</span></span>

- <span data-ttu-id="9e9c4-112"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>Ya da <xref:System.Text.UTF7Encoding> kendi protokolde veya dosya biçimindeyse kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="9e9c4-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="9e9c4-113">Veya kullanarak geçiş <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> yapın <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="9e9c4-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="9e9c4-114">UTF-8 endüstri standardıdır ve diller, işletim sistemleri ve çalışma zamanları genelinde yaygın olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="9e9c4-115">UTF-8 kullanımı, kodunuzun gelecekteki bakımını kolaylaştırır ve ekosisteminin geri kalanı ile daha birlikte çalışabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="9e9c4-116">Bir örneği karşılaştırıyorsanız <xref:System.Text.Encoding> <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="9e9c4-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="9e9c4-117">Bunun yerine, iyi bilinen UTF-7 kod sayfasına karşı bir denetim gerçekleştirmeyi göz önünde bulundurun `65000` .</span><span class="sxs-lookup"><span data-stu-id="9e9c4-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="9e9c4-118">Kod sayfasıyla karşılaştırıldığında, uyarıyı önleyin ve aynı zamanda türü bir veya alt sınıfı olarak çağırırın gibi bazı uç durumları da idare edersiniz `new UTF7Encoding()` .</span><span class="sxs-lookup"><span data-stu-id="9e9c4-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="9e9c4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e9c4-119">See also</span></span>

- [<span data-ttu-id="9e9c4-120">UTF-7 kod yolları kullanımdan kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="9e9c4-120">UTF-7 code paths are obsolete</span></span>](core-libraries/5.0/utf-7-code-paths-obsolete.md)
