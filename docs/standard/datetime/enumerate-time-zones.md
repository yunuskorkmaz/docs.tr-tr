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
ms.openlocfilehash: afc3b57659dd6719f72cefba8a6d2f1abe08c0d0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106645"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma

Belirlenen saat dilimiyle başarıyla çalışarak, bu saat dilimi hakkındaki bilgilerin sistem tarafından kullanılabilir olmasını gerektirir. Windows XP ve Windows Vista işletim sistemleri bu bilgileri kayıt defterine depolar. Ancak, dünyanın tamamında bulunan toplam saat dilimi sayısı büyük olsa da, kayıt defteri yalnızca bir alt kümesiyle ilgili bilgiler içerir. Ayrıca, kayıt defteri içeriği hem bilinçli hem de yanlışlıkla değişikliğe tabi olan dinamik bir yapıdır. Sonuç olarak, bir uygulama belirli bir saat diliminin bir sistemde tanımlandığını ve kullanılabildiğini her zaman varsayamaz. Saat dilimi bilgileri uygulamalarını kullanan birçok uygulama için ilk adım, gerekli saat dilimlerinin yerel sistemde kullanılabilir olup olmadığını belirlemektir veya kullanıcıya seçilecek saat dilimlerinin bir listesini vermektir. Bu, bir uygulamanın yerel bir sistemde tanımlanan saat dilimlerini numaralandırmasını gerektirir.

> [!NOTE]
> Bir uygulama, yerel bir sistemde tanımlanmayan belirli bir saat dilimi varlığını kullanıyorsa, uygulama, saat dilimi hakkındaki bilgileri serileştirerek ve serisini kaldırarak varlığını garanti edebilir. Daha sonra saat dilimi, uygulama kullanıcısının onu seçmesini sağlamak için bir liste denetimine eklenebilir. Ayrıntılar için bkz [. nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) kaydedin ve [şunları yapın: Katıştırılmış bir kaynaktan](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)saat dilimlerini geri yükleyin.

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Yerel sistemde mevcut olan saat dilimlerini listelemek için

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Yöntemi, genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> bir <xref:System.TimeZoneInfo> nesne koleksiyonu döndürür. Koleksiyondaki girişler, özelliklerine göre <xref:System.TimeZoneInfo.DisplayName%2A> sıralanır. Örneğin:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Bir <xref:System.TimeZoneInfo> C# `For Each`döngüsü (ın) veya a... kullanarak koleksiyondaki tek tek nesneleri numaralandırın. `foreach``Next` Loop (Visual Basic) ve her bir nesne üzerinde gerekli işlemleri gerçekleştirin. Örneğin, aşağıdaki kod adım 1 ' de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> döndürülen <xref:System.TimeZoneInfo> nesnelerin koleksiyonunu numaralandırır ve konsolundaki her bir saat diliminin görünen adını listeler.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Kullanıcıya yerel sistemde mevcut saat dilimlerinin bir listesini sunmak için

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Yöntemi, genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> bir <xref:System.TimeZoneInfo> nesne koleksiyonu döndürür.

2. Adım 1 `DataSource` ' de döndürülen koleksiyonu bir Windows Forms veya ASP.net List denetiminin özelliğine atayın.

3. Kullanıcının seçtiği <xref:System.TimeZoneInfo> nesneyi alın.

Örnek, bir Windows uygulaması için bir çizim sağlar.

## <a name="example"></a>Örnek

Örnek, bir liste kutusunda bir sistemde tanımlanan saat dilimlerini görüntüleyen bir Windows uygulaması başlatır. Örnek daha sonra Kullanıcı tarafından seçilen zaman dilimi nesnesinin <xref:System.TimeZoneInfo.DisplayName%2A> özelliğinin değerini içeren bir iletişim kutusu görüntüler.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Çoğu <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> liste denetimleri (veya <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> denetimi gibi), koleksiyon <xref:System.Collections.IEnumerable> arabirimini uyguladığı sürece, özelliklerine bir nesne değişkenleri `DataSource` koleksiyonu atamanıza olanak tanır. (Genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıf bunu yapar.) Koleksiyonda tek bir nesneyi göstermek için denetim, nesneyi temsil etmek için kullanılan dizeyi ayıklamak `ToString` için bu nesnenin yöntemini çağırır. <xref:System.TimeZoneInfo> Nesneler söz konusu olduğunda `ToString` , yöntemi <xref:System.TimeZoneInfo> nesnenin görünen adını ( <xref:System.TimeZoneInfo.DisplayName%2A> özelliğinin değeri) döndürür.

> [!NOTE]
> Liste denetimleri bir nesnenin `ToString` yöntemini çağırdığından, denetime bir nesne <xref:System.TimeZoneInfo> koleksiyonu atayabilir, denetimin her <xref:System.TimeZoneInfo> nesne için anlamlı bir ad görüntülemesini ve kullanıcının seçtiği nesneyi alabilmenizi sağlayabilirsiniz. Bu, koleksiyondaki her nesne için bir dize ayıklama gereksinimini ortadan kaldırır, dizeyi denetimin `DataSource` özelliğine atanan bir koleksiyona atar, kullanıcının seçtiği dizeyi alır ve sonra nesneyi ayıklamak için bu dizeyi kullanır burada açıklanmıştır. 

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  <xref:System>( C# kodda)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa Kaydet](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
