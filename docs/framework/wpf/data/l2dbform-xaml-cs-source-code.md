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
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="34f20-102">L2DBForm.xaml.cs kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="34f20-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="34f20-103">Bu sayfa, C# *L2DBForm.xaml.cs*dosyasındaki kaynak kodun içeriğini ve açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="34f20-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="34f20-104">Bu dosyada bulunan L2XDBForm kısmi sınıfı üç mantıksal bölüme ayrılabilir: veri üyeleri ve `OnRemove` ve `OnAddBook` düğme olay işleyicileri ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="34f20-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="34f20-105">Veri üyeleri</span><span class="sxs-lookup"><span data-stu-id="34f20-105">Data members</span></span>

<span data-ttu-id="34f20-106">Bu sınıfı *L2DBForm. xaml*içinde kullanılan pencere kaynaklarıyla ilişkilendirmek için iki özel veri üyesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34f20-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="34f20-107">`myBooks` ad alanı değişkeni `"http://www.mybooks.com"`başlatılır.</span><span class="sxs-lookup"><span data-stu-id="34f20-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="34f20-108">Üye `bookList`, Oluşturucu içinde *L2DBForm. xaml* içindeki CDATA dizesine aşağıdaki satırla başlatılır:</span><span class="sxs-lookup"><span data-stu-id="34f20-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="34f20-109">OnAddBook olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="34f20-109">OnAddBook event handler</span></span>

<span data-ttu-id="34f20-110">Bu yöntem, aşağıdaki üç deyimi içerir:</span><span class="sxs-lookup"><span data-stu-id="34f20-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="34f20-111">İlk koşullu ifade, giriş doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34f20-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="34f20-112">İkinci ifade, kullanıcının **Yeni kitap** kullanıcı ARABIRIMI (UI) Ekle bölümünde girdiği dize değerlerinden yeni bir <xref:System.Xml.Linq.XElement> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34f20-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="34f20-113">Son ifade, bu yeni kitap öğesini *L2DBForm. xaml*içindeki veri sağlayıcısına ekler.</span><span class="sxs-lookup"><span data-stu-id="34f20-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="34f20-114">Sonuç olarak, dinamik veri bağlama Kullanıcı arabirimini bu yeni öğe ile otomatik olarak güncelleştirir; Ek Kullanıcı tarafından sağlanan kod gerekmez.</span><span class="sxs-lookup"><span data-stu-id="34f20-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="34f20-115">OnRemove olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="34f20-115">OnRemove event handler</span></span>

<span data-ttu-id="34f20-116">`OnRemove` işleyicisi iki nedenden dolayı `OnAddBook` işleyicisinden daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="34f20-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="34f20-117">İlk olarak, Ham XML korunmuş boşluk içerdiğinden, newlines ile eşleşen bir kitap girişi de kaldırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34f20-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="34f20-118">İkincisi, bir kolaylık olması halinde, silinen öğede bulunan seçim, listedeki bir öncekine sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="34f20-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="34f20-119">Ancak, seçili kitap öğesini kaldırmanın temel çalışması yalnızca iki deyim tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="34f20-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="34f20-120">İlk olarak, liste kutusunda şu anda seçili olan öğeyle ilişkili kitap öğesi alınır:</span><span class="sxs-lookup"><span data-stu-id="34f20-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="34f20-121">Ardından, bu öğe veri sağlayıcısından silinir:</span><span class="sxs-lookup"><span data-stu-id="34f20-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="34f20-122">Dinamik veri bağlama, programın Kullanıcı arabiriminin otomatik olarak güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="34f20-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="34f20-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="34f20-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="34f20-124">Kod</span><span class="sxs-lookup"><span data-stu-id="34f20-124">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="34f20-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34f20-125">Comments</span></span>

<span data-ttu-id="34f20-126">Bu işleyiciler için ilişkili XAML kaynağı için bkz [. L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="34f20-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34f20-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34f20-127">See also</span></span>

- [<span data-ttu-id="34f20-128">İzlenecek yol: LinqToXmlDataBinding örneği</span><span class="sxs-lookup"><span data-stu-id="34f20-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="34f20-129">L2DBForm.xaml kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="34f20-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
