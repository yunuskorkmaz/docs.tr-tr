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
ms.openlocfilehash: 5e04aa1a1d209074dbdadcb1df089e31efa84ded
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556724"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Nasıl yapılır: ObservableCollection Oluşturma ve Bağlama
Bu örnek nasıl oluşturulacağını ve türetilen bir koleksiyon bağlamak gösterir <xref:System.Collections.ObjectModel.ObservableCollection%601> öğeleri eklendiğinde veya kaldırıldığında bildirimler sağlayan bir koleksiyonu sınıfının sınıfı.  
  
## <a name="example"></a>Örnek  
 Uygulaması aşağıdaki örnekte bir `NameList` koleksiyonu:  
  
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
  
 Koleksiyon, yaptığınız diğer ile aynı şekilde bağlama için kullanılabilir hale getirebilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] açıklandığı gibi nesneleri [veri kullanılabilir yap XAML'de bağlama için](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md). Örneğin, koleksiyonda örneğini oluşturabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve aşağıda gösterildiği gibi bir kaynak olarak bir koleksiyon belirtin:  
  
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
  
 Ardından koleksiyonu bağlayabilirsiniz:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Tanımını `NameItemTemplate` burada gösterilmiyor.  
  
> [!NOTE]
>  Koleksiyonunuz nesneleri bölümünde açıklanan gereksinimleri karşılaması gerekir [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md). Kullanıyorsanız, özellikle <xref:System.Windows.Data.BindingMode.OneWay> veya <xref:System.Windows.Data.BindingMode.TwoWay> (örneğin, istediğiniz, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynak özellikleri dinamik olarak değiştiğinde güncelleştirmek için), gibiuygunözellikdeğiştirildibildirimmekanizmasıuygulamalıdır<xref:System.ComponentModel.INotifyPropertyChanged>arabirimi.  
  
 Koleksiyonları bölümünde bağlamayı daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görünümde Verileri Sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Görünümde Veri Filtreleme](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
