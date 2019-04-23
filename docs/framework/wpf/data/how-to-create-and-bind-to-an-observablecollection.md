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
ms.openlocfilehash: 45f8b097bfdb8d3d7994e53ea05146aa6de0fc21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188441"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Nasıl yapılır: ObservableCollection Oluşturma ve Bağlama
Bu örnekte, oluşturma ve türeyen bir koleksiyona bağlama işlemi gösterilmektedir <xref:System.Collections.ObjectModel.ObservableCollection%601> bildirimleri öğeleri eklendiğinde veya kaldırıldığında sağlayan bir koleksiyon sınıf olan sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek uygulamasını gösterir. bir `NameList` koleksiyonu:  
  
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
  
 Koleksiyon, başka şekilde bağlama için kullanılabilir hale getirebilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] açıklandığı gibi nesneleri [olun veri kullanılabilir için XAML bağlamasında](how-to-make-data-available-for-binding-in-xaml.md). Örneğin, koleksiyon içinde oluşturabileceğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve burada gösterildiği gibi bir kaynak olarak koleksiyonu belirtin:  
  
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
  
 Ardından koleksiyonuna bağlayabilirsiniz:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Tanımı `NameItemTemplate` burada gösterilmez.  
  
> [!NOTE]
>  Koleksiyonunuzdaki nesneleri açıklanan gereksinimleri karşılaması gerekir [bağlama kaynaklarına genel bakış](binding-sources-overview.md). Kullanıyorsanız özellikle <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> (örneğin, istediğiniz, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynak özelliklerini dinamik olarak değiştirdiğinizde güncelleştirmek için), uygun özellik değiştirildi bildirim mekanizması gibiuygulamalıdır<xref:System.ComponentModel.INotifyPropertyChanged>arabirimi.  
  
 Daha fazla bilgi için bkz koleksiyonları bölümüne bağlama [Data Binding Overview](data-binding-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görünümde Verileri Sıralama](how-to-sort-data-in-a-view.md)
- [Görünümde Veri Filtreleme](how-to-filter-data-in-a-view.md)
- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
