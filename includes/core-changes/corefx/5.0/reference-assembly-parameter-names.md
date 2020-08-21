---
ms.openlocfilehash: abcab63b5a90a70cc9dfabb031e94ce379e5471b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720219"
---
### <a name="parameter-names-changed-in-reference-assemblies"></a><span data-ttu-id="9bd9c-101">Başvuru derlemelerindeki parametre adları değiştirildi</span><span class="sxs-lookup"><span data-stu-id="9bd9c-101">Parameter names changed in reference assemblies</span></span>

<span data-ttu-id="9bd9c-102">Bazı başvuru derleme parametresi adları, uygulama derlemelerindeki parametre adlarıyla eşleşecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9bd9c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9bd9c-103">Change description</span></span>

<span data-ttu-id="9bd9c-104">Önceki .NET sürümlerinde, bazı [Başvuru derleme](../../../../docs/standard/assembly/reference-assemblies.md) parametresi adları, uygulama derlemesinde karşılık gelen parametrelere farklıdır.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-104">In previous .NET versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="9bd9c-105">Bu, adlandırılmış bağımsız değişkenler ve yansıma kullanılırken soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="9bd9c-106">.NET 5,0 ' de, bu eşleşmeyen parametre adları, başvuru derlemelerinde, uygulama derlemelerindeki karşılık gelen parametre adlarıyla tam olarak eşleşecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-106">In .NET 5.0, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="9bd9c-107">Aşağıdaki tabloda, değiştirilen API 'Ler ve parametre adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="9bd9c-108">API</span><span class="sxs-lookup"><span data-stu-id="9bd9c-108">API</span></span> | <span data-ttu-id="9bd9c-109">Eski parametre adı</span><span class="sxs-lookup"><span data-stu-id="9bd9c-109">Old parameter name</span></span> | <span data-ttu-id="9bd9c-110">Yeni parametre adı</span><span class="sxs-lookup"><span data-stu-id="9bd9c-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=nameWithType> | `stms` | `stmts` |
| <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=nameWithType> | `authType` | `authenticationType` |
| <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=nameWithType> | `o` | `obj` |
| <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=nameWithType> | `value` | `obj` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=nameWithType> | `value` | `strInput` |

#### <a name="reason-for-change"></a><span data-ttu-id="9bd9c-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9bd9c-111">Reason for change</span></span>

<span data-ttu-id="9bd9c-112">Parametre adları tutarlılık için değiştirilmiştir ve adlandırılmış bağımsız değişkenler ve yansıma kullanılırken hatalardan kaçınmak için.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9bd9c-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9bd9c-113">Version introduced</span></span>

<span data-ttu-id="9bd9c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="9bd9c-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9bd9c-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9bd9c-115">Recommended action</span></span>

<span data-ttu-id="9bd9c-116">Bir parametre adı değişikliği nedeniyle bir derleyici hatasıyla karşılaşırsanız parametre adını uygun şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9bd9c-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="9bd9c-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="9bd9c-117">Category</span></span>

<span data-ttu-id="9bd9c-118">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="9bd9c-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9bd9c-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9bd9c-119">Affected APIs</span></span>

- <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=fullName>
- <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)>
- <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=fullName>
- <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=fullName>
- <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Boolean)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Int32,System.Boolean)`
- `M:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)`
- `M:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})`
- `M:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String)`
- `M:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.Normalize(System.String)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)`
- `M:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)`
- `M:System.Drawing.Icon.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Drawing.Image.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`

-->
