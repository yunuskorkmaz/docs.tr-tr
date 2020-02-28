---
title: 'Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: aa8962c8aea208778983610041937dc3f75c1f1e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159448"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma

Belirlenen saat dilimiyle başarıyla çalışarak, bu saat dilimi hakkındaki bilgilerin sistem tarafından kullanılabilir olmasını gerektirir. Windows XP ve Windows Vista işletim sistemleri bu bilgileri kayıt defterine depolar. Ancak, dünyanın tamamında bulunan toplam saat dilimi sayısı büyük olsa da, kayıt defteri yalnızca bir alt kümesiyle ilgili bilgiler içerir. Ayrıca, kayıt defteri içeriği hem bilinçli hem de yanlışlıkla değişikliğe tabi olan dinamik bir yapıdır. Sonuç olarak, bir uygulama belirli bir saat diliminin bir sistemde tanımlandığını ve kullanılabildiğini her zaman varsayamaz. Saat dilimi bilgileri uygulamalarını kullanan birçok uygulama için ilk adım, gerekli saat dilimlerinin yerel sistemde kullanılabilir olup olmadığını belirlemektir veya kullanıcıya seçilecek saat dilimlerinin bir listesini vermektir. Bu, bir uygulamanın yerel bir sistemde tanımlanan saat dilimlerini numaralandırmasını gerektirir.

> [!NOTE]
> Bir uygulama, yerel bir sistemde tanımlanmayan belirli bir saat dilimi varlığını kullanıyorsa, uygulama, saat dilimi hakkındaki bilgileri serileştirerek ve serisini kaldırarak varlığını garanti edebilir. Daha sonra saat dilimi, uygulama kullanıcısının onu seçmesini sağlamak için bir liste denetimine eklenebilir. Ayrıntılar için bkz. [nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: bir katıştırılmış kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Yerel sistemde mevcut olan saat dilimlerini listelemek için

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemini çağırın. Yöntemi, <xref:System.TimeZoneInfo> nesnelerin genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu döndürür. Koleksiyondaki girişler <xref:System.TimeZoneInfo.DisplayName%2A> özelliklerine göre sıralanır. Örnek:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Bir `foreach` döngüsü (içinde C#) veya `For Each`... kullanarak koleksiyondaki tek <xref:System.TimeZoneInfo> nesnelerini numaralandırın`Next` Loop (Visual Basic) ve her bir nesne üzerinde gerekli işlemleri gerçekleştirin. Örneğin, aşağıdaki kod, 1. adımda döndürülen <xref:System.TimeZoneInfo> nesnelerinin <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu numaralandırır ve konsolundaki her bir saat diliminin görünen adını listeler.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Kullanıcıya yerel sistemde mevcut saat dilimlerinin bir listesini sunmak için

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemini çağırın. Yöntemi, <xref:System.TimeZoneInfo> nesnelerin genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonunu döndürür.

2. Adım 1 ' de döndürülen koleksiyonu bir Windows Forms veya ASP.NET List denetiminin `DataSource` özelliğine atayın.

3. Kullanıcının seçtiği <xref:System.TimeZoneInfo> nesnesini alın.

Örnek, bir Windows uygulaması için bir çizim sağlar.

## <a name="example"></a>Örnek

Örnek, bir liste kutusunda bir sistemde tanımlanan saat dilimlerini görüntüleyen bir Windows uygulaması başlatır. Örnek daha sonra Kullanıcı tarafından seçilen zaman dilimi nesnesinin <xref:System.TimeZoneInfo.DisplayName%2A> özelliğinin değerini içeren bir iletişim kutusu görüntüler.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Çoğu liste denetimleri (<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> veya <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> denetimi), bu koleksiyonun <xref:System.Collections.IEnumerable> arabirimini uyguladığı sürece `DataSource` özelliklerine bir nesne değişkenleri koleksiyonu atamanıza olanak tanır. (Genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıfı bunu yapar.) Koleksiyonda tek bir nesneyi göstermek için denetim, nesneyi temsil etmek için kullanılan dizeyi ayıklamak için bu nesnenin `ToString` yöntemini çağırır. <xref:System.TimeZoneInfo> nesneler söz konusu olduğunda, `ToString` yöntemi <xref:System.TimeZoneInfo> nesnenin görünen adını döndürür (<xref:System.TimeZoneInfo.DisplayName%2A> özelliğinin değeri).

> [!NOTE]
> Liste denetimleri bir nesnenin `ToString` yöntemini çağırdığından, denetime <xref:System.TimeZoneInfo> nesnelerden oluşan bir koleksiyon atayabilir, denetimin her nesne için anlamlı bir ad görüntülemesini ve kullanıcının seçtiği <xref:System.TimeZoneInfo> nesnesini almanızı sağlayabilirsiniz. Bu, koleksiyondaki her bir nesne için bir dize ayıklama gereksinimini ortadan kaldırır, dizeyi denetimin `DataSource` özelliğine atanan bir koleksiyona atar, kullanıcının seçtiği dizeyi alır ve ardından bu dizeyi kullanarak açıkladığı nesneyi ayıklar.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  <xref:System> ( C# kodda)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
