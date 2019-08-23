---
title: 'Nasıl yapılır: ObservableCollection Oluşturma ve Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 8db9f2051a0401e01f233f9c959e015eb657bdac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965471"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Nasıl yapılır: ObservableCollection Oluşturma ve Bağlama
Bu örnek, öğe eklendiğinde veya kaldırıldığında bildirim sağlayan bir koleksiyon sınıfı olan <xref:System.Collections.ObjectModel.ObservableCollection%601> sınıfından türetilen bir koleksiyonun nasıl oluşturulacağını ve bağlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `NameList` koleksiyonun uygulamasını göstermektedir:  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 [VERILERI xaml 'de bağlamaya uygun hale getirme](how-to-make-data-available-for-binding-in-xaml.md)bölümünde açıklandığı gibi, koleksiyonu diğer ortak dil çalışma zamanı (CLR) nesneleriyle aynı şekilde bağlama için kullanılabilir hale getirebilirsiniz. Örneğin, içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] koleksiyonu örnekleyebilirsiniz ve koleksiyonu aşağıda gösterildiği gibi bir kaynak olarak belirtebilirsiniz:  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 Daha sonra koleksiyona bağlayabilirsiniz:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Tanımı `NameItemTemplate` burada gösterilmez.  
  
> [!NOTE]
> Koleksiyonunuzdaki nesnelerin [bağlama kaynaklarına genel bakış](binding-sources-overview.md)bölümünde açıklanan gereksinimleri karşılaması gerekir. Özellikle, veya <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> kullanıyorsanız ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Örneğin, kaynak özellikleri dinamik olarak değiştiğinde güncelleştirilmesini istiyorsanız), gibi uygun bir özellik değiştirilmiş bildirim mekanizması <xref:System.ComponentModel.INotifyPropertyChanged>uygulamanızgerekirarabirim.  
  
 Daha fazla bilgi için [veri bağlamaya genel bakış](data-binding-overview.md)konusundaki koleksiyonlara bağlama bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görünümde Verileri Sıralama](how-to-sort-data-in-a-view.md)
- [Görünümde Veri Filtreleme](how-to-filter-data-in-a-view.md)
- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
