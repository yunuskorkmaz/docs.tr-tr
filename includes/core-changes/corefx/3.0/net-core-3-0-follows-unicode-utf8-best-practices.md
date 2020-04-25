---
ms.openlocfilehash: becae23cd810623bbb33c693b707c2d4735aeece
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158493"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="24d25-101">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="24d25-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="24d25-102">Sınıf, <xref:System.Text.UTF8Encoding> bir bayt karakter dönüştürme işlemi sırasında hatalı BIÇIMLENDIRILMIŞ bir UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesindeki ' ' (U + FFFD değiştirme karakteri) karakteriyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="24d25-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="24d25-103">.NET Core 3,0, .NET Core 'un önceki sürümlerinden ve .NET Framework dönüştürme işlemi sırasında bu değişikliği gerçekleştirmek için en iyi Unicode yöntemi izleyerek farklıdır.</span><span class="sxs-lookup"><span data-stu-id="24d25-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="24d25-104">Bu, yeni <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> ve <xref:System.Text.Rune?displayProperty=nameWithType> türleri dahil olmak üzere .net genelinde UTF-8 işlemesini geliştirmenin daha büyük bir çaba parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="24d25-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="24d25-105">Türe <xref:System.Text.UTF8Encoding> , Yeni tanıtılan türlerle tutarlı bir çıkış üretmesi için, bu tür gelişmiş hata işleme mekanizması verildi.</span><span class="sxs-lookup"><span data-stu-id="24d25-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24d25-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="24d25-106">Change description</span></span>

<span data-ttu-id="24d25-107">.NET Core 3,0 ile başlayarak, baytları karakterlere dönüştürme sırasında <xref:System.Text.UTF8Encoding> sınıf, Unicode en iyi uygulamalarına göre karakter değiştirme işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="24d25-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="24d25-108">Kullanılan değiştirme mekanizması, _U + FFFD Substitution alt bölümlerinin_başlığı altında bulunan başlık Içindeki [Unicode standart, sürüm 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) ile açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="24d25-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="24d25-109">Bu davranış _yalnızca_ , giriş bayt dizisi hatalı biçimlendirilmiş UTF-8 verileri içerdiğinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="24d25-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="24d25-110">Ek olarak, <xref:System.Text.UTF8Encoding> örneği ile `throwOnInvalidBytes: true`oluşturulmuşsa, `UTF8Encoding` örnek U + FFFD yerini almak yerine geçersiz giriş üzerinde throw olmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="24d25-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="24d25-111">`UTF8Encoding` Oluşturucu hakkında daha fazla bilgi için bkz <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>..</span><span class="sxs-lookup"><span data-stu-id="24d25-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="24d25-112">Aşağıdaki tabloda, bu değişikliğin geçersiz bir 3 bayt girişi ile etkisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="24d25-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="24d25-113">Hatalı biçimlendirilmiş 3 baytlık giriş</span><span class="sxs-lookup"><span data-stu-id="24d25-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="24d25-114">.NET Core 3,0 öncesi çıkış</span><span class="sxs-lookup"><span data-stu-id="24d25-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="24d25-115">.NET Core 3,0 ile başlayan çıkış</span><span class="sxs-lookup"><span data-stu-id="24d25-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="24d25-116">`[ FFFD FFFD ]`(2 karakterlik çıkış)</span><span class="sxs-lookup"><span data-stu-id="24d25-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="24d25-117">`[ FFFD FFFD FFFD ]`(3 karakterlik çıkış)</span><span class="sxs-lookup"><span data-stu-id="24d25-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="24d25-118">3-char çıktısı, daha önce bağlantılı Unicode standart PDF 'nin _3-9 tablosuna_ göre tercih edilen çıktıdır.</span><span class="sxs-lookup"><span data-stu-id="24d25-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24d25-119">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="24d25-119">Version introduced</span></span>

<span data-ttu-id="24d25-120">3,0</span><span class="sxs-lookup"><span data-stu-id="24d25-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24d25-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="24d25-121">Recommended action</span></span>

<span data-ttu-id="24d25-122">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="24d25-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="24d25-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="24d25-123">Category</span></span>

<span data-ttu-id="24d25-124">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="24d25-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24d25-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="24d25-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
