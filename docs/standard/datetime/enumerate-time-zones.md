---
title: 'Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697cd40482aee73fd150359acb710ffc258c3df2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518416"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma

Başarıyla atanan bir saat dilimi ile çalışma, saat dilimi bilgilerini sistemi için kullanılabilir olmasını gerektirir. Windows XP ve Windows Vista işletim sistemleri, bu bilgileri kayıt defterinde depolar. Ancak, dünyanın her yerinde mevcut saat dilimlerini toplam sayısı büyük olsa da, kayıt defteri bunları yalnızca bir alt kümesi hakkında bilgi içerir. Ayrıca, kayıt defterini içerikleri hem kasıtlı hem de yanlışlıkla değişikliğe tabi olduğu bir dinamik yapısıdır. Sonuç olarak, bir uygulama her zaman belirli bir saat dilimini tanımlanan ve mevcut bir sistemde olduğunu varsayamazsınız. Saat dilimi bilgileri uygulamaları kullanan birçok uygulama için ilk adımı, gerekli saat dilimlerini yerel sistemde kullanılabilir olup olmadığını belirlemek için veya kullanıcı seçmek için saat dilimlerinin listesini vermek için ' dir. Bu, bir uygulamanın yerel sistemde tanımlanan saat dilimlerini numaralandırma gerektirir.

> [!NOTE]
> Bir uygulamanın yerel bir sistemde tanımlı değil belirli bir saat dilimi olup olmamasına dayanıyorsa, uygulama tarafından seri hale getirme ve saat dilimi bilgilerini seri durumdan çıkarılırken varlığını emin olabilirsiniz. Uygulama kullanıcısı seçebilmeniz için liste denetimi saat dilimini sonra eklenebilir. Ayrıntılar için bkz [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Yerel sistemde mevcut saat dilimlerini numaralandırma

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Genel yöntem döndürür <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu <xref:System.TimeZoneInfo> nesneleri. Koleksiyon girişlere göre sıralanır kendi <xref:System.TimeZoneInfo.DisplayName%2A> özelliği. Örneğin:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Tek tek listeleme <xref:System.TimeZoneInfo> kullanarak koleksiyonundaki nesneleri bir `foreach` döngüde (C#) veya bir `For Each`...`Next` (Visual Basic'te) döngü ve her bir nesneye gerekli herhangi bir işlem gerçekleştirin. Örneğin, aşağıdaki kod numaralandırır <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu <xref:System.TimeZoneInfo> 1. adım, döndürülen nesneleri ve her bir saat dilimi konsolunda görünen adını listeler.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Yerel sistemdeki saat dilimlerinin listesini içeren kullanıcı sunmak için

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Genel yöntem döndürür <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu <xref:System.TimeZoneInfo> nesneleri.

2. Adım 1'de döndürülen koleksiyon atama `DataSource` özelliği bir Windows forms veya ASP.NET denetim listesi.

3. Alma <xref:System.TimeZoneInfo> kullanıcının seçtiği bir nesne.

Örneğin, bir Windows uygulaması için bir gösterim sağlar.

## <a name="example"></a>Örnek

Örneğin, bir liste kutusunda bir sistemde tanımlanan saat dilimlerini görüntüleyen bir Windows uygulaması başlatır. Bu örnek, ardından değerini içeren bir iletişim kutusu görüntüler <xref:System.TimeZoneInfo.DisplayName%2A> kullanıcı tarafından seçilen saat dilimi nesnesinin özelliği.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

En çok, denetimleri listesi (gibi <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> veya <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> denetimi), nesne değişkenleri koleksiyonu atamanıza olanak sağlamak kendi `DataSource` özelliği o koleksiyon uygulayan sürece <xref:System.Collections.IEnumerable> arabirimi. (Genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıfı bunu yapar.) Koleksiyondaki tek bir nesneyi görüntülemek için bu nesnenin denetim çağrıları `ToString` nesneyi göstermek için kullanılan dize ayıklamak için yöntemi. Durumunda, <xref:System.TimeZoneInfo> nesneleri `ToString` yöntemi döndürür <xref:System.TimeZoneInfo> nesnenin görünen ad (değeri kendi <xref:System.TimeZoneInfo.DisplayName%2A> özelliği).

> [!NOTE]
> Bir nesnenin liste denetimleri çağırmak için `ToString` yöntemi, bir koleksiyonu atayabilirsiniz <xref:System.TimeZoneInfo> nesneler denetime sahip görünen her nesne için anlamlı bir ad ve alma denetimi <xref:System.TimeZoneInfo> kullanıcının seçtiği nesne. Bu koleksiyondaki her nesne için bir dize ayıklayın, dize denetimin hangi sırayla atanır bir koleksiyonla ilişkilendirin gereğini ortadan kaldırıyor `DataSource` özelliği, kullanıcının seçtiği dizesi alma ve sonra nesneyi ayıklamak için şu dizeyi kullanın BT'nin açıklar. 

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Şu ad alanlarından alınan olduğunu:

  <xref:System> (C# kodu)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
