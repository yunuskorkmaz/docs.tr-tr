---
title: 'Son değişiklik: null yapılabilir başvuru türü ek açıklama değişiklikleri'
description: Bazı null yapılabilir başvuru türü ek açıklamaların değiştiği çekirdek .NET kitaplıklarında .NET 6,0 son değişikliği hakkında bilgi edinin.
ms.date: 02/11/2021
ms.openlocfilehash: 7e3f1cbc5bff7814988ec5d16027838598188e9a
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206467"
---
# <a name="changes-to-nullable-reference-type-annotations"></a>Null yapılabilir başvuru türü ek açıklamalarına yapılan değişiklikler

.NET 6,0 ' de, .NET kitaplıklarında bazı null olabilme ek açıklamaları değişmiştir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, bazı Nullable başvuru türü ek açıklamaları yanlıştır ve derleme uyarıları yok ya da yanlış olabilir. .NET 6,0 ' den başlayarak, daha önce uygulanan bazı ek açıklamalar güncelleştirilmiştir. Yeni derleme uyarıları üretilecektir ve etkilenen API 'Ler için yanlış derleme uyarıları üretilmez.

Bu değişikliklerin bazıları yeni derleme zamanı uyarılarına yol açacağından, bu değişikliklerden bazıları *kesiliyor* olarak kabul edilir. .NET 6,0 ' e geçirdiğinizde, bu API 'Lere başvuran kodun güncellenmesi gerekecektir.

Bu sayfada, parçalama olarak kabul edilmeyen diğer değişiklikler de belgelenmiştir. Güncelleştirilmiş API 'Lere başvuruda bulunan tüm kodlar, artık gerekli olmayan işleçlerin veya pragmaların kaldırılması açısından yarar sağlayabilir.

## <a name="version-introduced"></a>Sunulan sürüm

6.0

## <a name="reason-for-change"></a>Değişiklik nedeni

.NET Core 3,0 ' den başlayarak, null olabilme ek açıklamaları .NET kitaplıklarına uygulandı. Çabadan itibaren, bu ek açıklamaların hataları tahmin edildi. Geri bildirim ve daha fazla test ile, etkilenen API 'Ler için null yapılabilir ek açıklamaların yanlış olduğu belirlendi. Güncelleştirilmiş ek açıklamalar, API 'Ler için null değer alabilirlik sözleşmelerini doğru şekilde temsil eder.

## <a name="recommended-action"></a>Önerilen eylem

Düzeltilen null olabilme sözleşmelerini yansıtmak için bu API 'Leri çağıran kodu güncelleştirin.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen API 'Ler listelenmektedir:

| API | Değişen | Kesme veya bölünemez | Sürüm eklendi |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | Özellik türü null yapılabilir | Yeni | Önizleme 1 |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | İkinci parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | İkinci parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | İkinci parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | Parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | `content` parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | `content` parametre türü null yapılabilir  | Ne | Önizleme 1 |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | `content` parametre türü null yapılabilir  | Ne | Önizleme 1 |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | İlk parametre türü null yapılabilir | Ne | Önizleme 1 |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | Dönüş türü null yapılabilir değil | Ne | Önizleme 1 |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` parametre türü null yapılabilir | Yeni | Önizleme 1 |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` parametre türü null yapılabilir | Yeni | Önizleme 1 |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` parametre türü null yapılabilir | Yeni | Önizleme 1 |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` parametre türü null yapılabilir | Yeni | Önizleme 1 |
| <xref:System.Net.HttpListenerContext.AcceptWebSocketAsync%2A?displayProperty=fullName> | `subProtocol` parametre türü null yapılabilir | Ne | Önizleme 2 |
| Geçersiz kılan <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> ve [çok sayıda diğerlerini döndüren `bool` ](https://github.com/dotnet/runtime/pull/47598/files) Yöntemler | `[NotNullWhen(true)]` ilk, null yapılabilir parametreye eklendi | Yeni | Önizleme 2 |

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core null yapılabilir başvuru türü ek açıklama değişiklikleri](../../aspnet-core/6.0/nullable-reference-type-annotations-changed.md)

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->
