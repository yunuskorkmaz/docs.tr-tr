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
ms.openlocfilehash: 8f1cc9d58bc0f169d458854eac6568caaa4481c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286138"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma

Belirlenen saat dilimiyle başarıyla çalışarak, bu saat dilimi hakkındaki bilgilerin sistem tarafından kullanılabilir olmasını gerektirir. Windows XP ve Windows Vista işletim sistemleri bu bilgileri kayıt defterine depolar. Ancak, dünyanın tamamında bulunan toplam saat dilimi sayısı büyük olsa da, kayıt defteri yalnızca bir alt kümesiyle ilgili bilgiler içerir. Ayrıca, kayıt defteri içeriği hem bilinçli hem de yanlışlıkla değişikliğe tabi olan dinamik bir yapıdır. Sonuç olarak, bir uygulama belirli bir saat diliminin bir sistemde tanımlandığını ve kullanılabildiğini her zaman varsayamaz. Saat dilimi bilgileri uygulamalarını kullanan birçok uygulama için ilk adım, gerekli saat dilimlerinin yerel sistemde kullanılabilir olup olmadığını belirlemektir veya kullanıcıya seçilecek saat dilimlerinin bir listesini vermektir. Bu, bir uygulamanın yerel bir sistemde tanımlanan saat dilimlerini numaralandırmasını gerektirir.

> [!NOTE]
> Bir uygulama, yerel bir sistemde tanımlanmayan belirli bir saat dilimi varlığını kullanıyorsa, uygulama, saat dilimi hakkındaki bilgileri serileştirerek ve serisini kaldırarak varlığını garanti edebilir. Daha sonra saat dilimi, uygulama kullanıcısının onu seçmesini sağlamak için bir liste denetimine eklenebilir. Ayrıntılar için bkz. [nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: bir katıştırılmış kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Yerel sistemde mevcut olan saat dilimlerini listelemek için

1. Yöntemini çağırın <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> . Yöntemi, genel bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nesne koleksiyonu döndürür <xref:System.TimeZoneInfo> . Koleksiyondaki girişler, özelliklerine göre sıralanır <xref:System.TimeZoneInfo.DisplayName%2A> . Örneğin:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <xref:System.TimeZoneInfo>Bir `foreach` döngüsü (C# ' de) veya bir... kullanarak koleksiyondaki tek tek nesneleri numaralandırın. `For Each``Next` Loop (Visual Basic) ve her bir nesne üzerinde gerekli işlemleri gerçekleştirin. Örneğin, aşağıdaki kod <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> Adım 1 ' de döndürülen nesnelerin koleksiyonunu numaralandırır ve konsolundaki her bir saat diliminin görünen adını listeler.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Kullanıcıya yerel sistemde mevcut saat dilimlerinin bir listesini sunmak için

1. Yöntemini çağırın <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> . Yöntemi, genel bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nesne koleksiyonu döndürür <xref:System.TimeZoneInfo> .

2. Adım 1 ' de döndürülen koleksiyonu `DataSource` bir Windows Forms veya ASP.net List denetiminin özelliğine atayın.

3. <xref:System.TimeZoneInfo>Kullanıcının seçtiği nesneyi alın.

Örnek, bir Windows uygulaması için bir çizim sağlar.

## <a name="example"></a>Örnek

Örnek, bir liste kutusunda bir sistemde tanımlanan saat dilimlerini görüntüleyen bir Windows uygulaması başlatır. Örnek daha sonra <xref:System.TimeZoneInfo.DisplayName%2A> Kullanıcı tarafından seçilen zaman dilimi nesnesinin özelliğinin değerini içeren bir iletişim kutusu görüntüler.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Çoğu liste denetimleri ( <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> veya <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> denetimi gibi), `DataSource` koleksiyon arabirimini uyguladığı sürece, özelliklerine bir nesne değişkenleri koleksiyonu atamanıza olanak tanır <xref:System.Collections.IEnumerable> . (Genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıf bunu yapar.) Koleksiyonda tek bir nesneyi göstermek için denetim, nesneyi `ToString` temsil etmek için kullanılan dizeyi ayıklamak için bu nesnenin yöntemini çağırır. Nesneler söz konusu olduğunda <xref:System.TimeZoneInfo> , `ToString` yöntemi <xref:System.TimeZoneInfo> nesnenin görünen adını ( <xref:System.TimeZoneInfo.DisplayName%2A> özelliğinin değeri) döndürür.

> [!NOTE]
> Liste denetimleri bir nesnenin yöntemini çağırdığından, `ToString` denetime bir nesne koleksiyonu atayabilir <xref:System.TimeZoneInfo> , denetimin her nesne için anlamlı bir ad görüntülemesini ve <xref:System.TimeZoneInfo> kullanıcının seçtiği nesneyi alabilmenizi sağlayabilirsiniz. Bu, koleksiyondaki her bir nesne için bir dize ayıklama gereksinimini ortadan kaldırır, dizeyi denetimin özelliğine atanan bir koleksiyona atayın `DataSource` , kullanıcının seçtiği dizeyi alın ve ardından bu dizeyi, açıkladığı nesneyi ayıklamak için kullanın.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  <xref:System>(C# kodunda)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](save-time-zones-to-an-embedded-resource.md)
- [Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md)
