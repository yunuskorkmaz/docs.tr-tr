---
title: L2DBForm.xaml.cs kaynak kodu
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920862"
---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs kaynak kodu

Bu sayfa, C# *L2DBForm.xaml.cs*dosyasındaki kaynak kodun içeriğini ve açıklamasını içerir. Bu dosyada bulunan L2XDBForm kısmi sınıfı üç mantıksal bölüme ayrılabilir: veri üyeleri ve `OnRemove` ve `OnAddBook` düğme olay işleyicileri ' ne tıklayın.

## <a name="data-members"></a>Veri üyeleri

Bu sınıfı *L2DBForm. xaml*içinde kullanılan pencere kaynaklarıyla ilişkilendirmek için iki özel veri üyesi kullanılır.

- `myBooks` ad alanı değişkeni `"http://www.mybooks.com"`başlatılır.

- Üye `bookList`, Oluşturucu içinde *L2DBForm. xaml* içindeki CDATA dizesine aşağıdaki satırla başlatılır:

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>OnAddBook olay işleyicisi

Bu yöntem, aşağıdaki üç deyimi içerir:

- İlk koşullu ifade, giriş doğrulaması için kullanılır.

- İkinci ifade, kullanıcının **Yeni kitap** kullanıcı ARABIRIMI (UI) Ekle bölümünde girdiği dize değerlerinden yeni bir <xref:System.Xml.Linq.XElement> oluşturur.

- Son ifade, bu yeni kitap öğesini *L2DBForm. xaml*içindeki veri sağlayıcısına ekler. Sonuç olarak, dinamik veri bağlama Kullanıcı arabirimini bu yeni öğe ile otomatik olarak güncelleştirir; Ek Kullanıcı tarafından sağlanan kod gerekmez.

## <a name="onremove-event-handler"></a>OnRemove olay işleyicisi

`OnRemove` işleyicisi iki nedenden dolayı `OnAddBook` işleyicisinden daha karmaşıktır. İlk olarak, Ham XML korunmuş boşluk içerdiğinden, newlines ile eşleşen bir kitap girişi de kaldırılmalıdır. İkincisi, bir kolaylık olması halinde, silinen öğede bulunan seçim, listedeki bir öncekine sıfırlanır.

Ancak, seçili kitap öğesini kaldırmanın temel çalışması yalnızca iki deyim tarafından gerçekleştirilir:

- İlk olarak, liste kutusunda şu anda seçili olan öğeyle ilişkili kitap öğesi alınır:

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- Ardından, bu öğe veri sağlayıcısından silinir:

    ```csharp
    selBook.Remove();
    ```

Dinamik veri bağlama, programın Kullanıcı arabiriminin otomatik olarak güncelleştirilmesini sağlar.

## <a name="example"></a>Örnek

### <a name="code"></a>Kod

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a>Açıklamalar

Bu işleyiciler için ilişkili XAML kaynağı için bkz [. L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: LinqToXmlDataBinding örneği](linq-to-xml-data-binding-sample.md)
- [L2DBForm.xaml kaynak kodu](l2dbform-xaml-source-code.md)
