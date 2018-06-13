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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfdc3993f6658ce5dc50050ed062c2de9d4cec29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579437"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma

Başarıyla atanan bir saat dilimi ile çalışma, saat dilimi bilgilerini sistemi için kullanılabilir olmasını gerektirir. Windows XP ve Windows Vista işletim sistemleri, kayıt defterinde bu bilgileri depolar. Ancak, dünyanın her yerinde mevcut saat dilimlerini toplam sayısı büyük olsa da, kayıt defteri bunları yalnızca bir alt hakkında bilgiler içerir. Ayrıca, kayıt defteri kasıtlı ve yanlışlıkla değiştirilebilir içeriği olan bir dinamik yapısıdır. Sonuç olarak, uygulama her zaman belirli bir saat dilimi tanımlı ve kullanılabilir bir sistemde olduğunu varsayın olamaz. İlk saat dilimi bilgileri uygulamaları pek çok uygulama gerekli saat dilimleri yerel sistem üzerinde kullanılabilir olup olmadığını belirlemek ya da kullanıcı seçmek için saat dilimleri listesini vermek için adımdır. Bu, bir uygulamanın yerel sistemde tanımlanan saat dilimlerini numaralandırma gerektirir.

> [!NOTE]
> Bir uygulamanın yerel sistemde tanımlı değil belirli bir saat dilimi varlığına dayalıysa, seri hale getirme ve seri durumdan saat dilimi bilgilerini uygulamanın varlığını emin olabilirsiniz. Uygulama kullanıcısı seçebilmesi saat dilimi sonra bir liste denetimini eklenebilir. Ayrıntılar için bkz [nasıl yapılır: Kaydet saat dilimlerini katıştırılmış kaynağa](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Yerel sistemdeki saat dilimlerini numaralandırma için

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Genel yöntem <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonu <xref:System.TimeZoneInfo> nesneleri. Koleksiyon girdileri göre sıralanır kendi <xref:System.TimeZoneInfo.DisplayName%2A> özelliği. Örneğin:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Tek tek listeleme <xref:System.TimeZoneInfo> kullanarak koleksiyonundaki nesneleri bir `foreach` döngüde (C# ' ta) veya bir `For Each`...`Next` (Visual Basic'te) döngü ve her nesne üzerinde gerekli herhangi bir işlem gerçekleştirin. Örneğin, aşağıdaki kodu numaralandırır <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonu <xref:System.TimeZoneInfo> nesne içinde döndürülen adım 1 ve her bir saat dilimi konsolunda görünen adını listeler.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Saat dilimleri yerel sistemde listesini içeren kullanıcı sunmak için

1. Çağrı <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> yöntemi. Genel yöntem <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> koleksiyonu <xref:System.TimeZoneInfo> nesneleri.

2. Adım 1'de döndürülen koleksiyon atamak `DataSource` özelliği bir Windows forms ya da ASP.NET denetim listesi.

3. Alma <xref:System.TimeZoneInfo> kullanıcının seçtiği nesnesi.

Örnek bir Windows uygulaması için bir çizim verilmektedir.

## <a name="example"></a>Örnek

Örnek bir liste kutusunda bir sistemde tanımlanan saat dilimlerini görüntüleyen bir Windows uygulaması başlatır. Örnek sonra değerini içeren bir iletişim kutusu görüntüler <xref:System.TimeZoneInfo.DisplayName%2A> kullanıcı tarafından seçilen saat dilimi nesnesinin özelliği.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

En, Denetim listesi (gibi <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> veya <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> denetimi) nesne değişkenleri koleksiyonu atamanızı izin kendi `DataSource` özelliği o koleksiyona uygulayan sürece <xref:System.Collections.IEnumerable> arabirimi. (Genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıfı yapar.) Koleksiyonda tek bir nesneyi görüntülemek için bu nesnenin denetimi çağırır `ToString` nesneyi göstermek için kullanılan dize ayıklamak için yöntem. Durumunda <xref:System.TimeZoneInfo> nesneleri `ToString` yöntemi döndürür <xref:System.TimeZoneInfo> nesnenin görünen adını (değerini kendi <xref:System.TimeZoneInfo.DisplayName%2A> özelliği).

> [!NOTE]
> Liste denetimleri nesnenin çağırması nedeniyle `ToString` yöntemi, bir koleksiyonu atayabilirsiniz <xref:System.TimeZoneInfo> denetim nesnelere sahip her nesne için anlamlı bir ad görüntülemek ve almak denetimi <xref:System.TimeZoneInfo> kullanıcının seçtiği nesnesi. Bu koleksiyondaki her nesne için bir dize ayıklamak, denetimin sırayla atanmış bir koleksiyon için dize Ata gereğini ortadan kaldırır `DataSource` özelliği, kullanıcı seçildi dizesi alma ve nesne ayıklamak için bu dizeyi kullanın Bu BT açıklar. 

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Şu ad alanlarından alınan olduğunu:

  <xref:System> (C# kodunda)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
